# Parameters Screwdriver Yaml
<details>
<summary>Screwdriver Keywords</summary>
parameter, parameters, parameters build, parameterized, parameterized build
</details>

`Parameters` are defined on the top level of `screwdriver.yaml`, see below as example.

## Definition
There are 2 ways of defining parameters, see

```yaml
paramters:
    nameA: "value1"
    nameB:
        value: "value2"
        description: "description of nameB"
```

**Parameters** is a dictionary which expects `key:value` pairs.

```yaml
nameA: "value1"
```

 `key: string` is a shorthand for writting as `key:value`

```yaml
nameA:
    value: "value1"
    description: ""
```

These two are identical with description to be an empty string

## Example
See [Screwdriver pipeline](https://cd.screwdriver.cd/pipelines/3449/events)

```yaml
shared:
    image: node:8

parameters:
    region: "us-west-1"
    az:
        value: "1"
        description: "default availability zone"

jobs:
    main:
        requires: [~pr, ~commit]
        steps:
            - step1: 'echo "Region: $(meta get parameters.region.value)"'
            - step2: 'echo "AZ: $(meta get parameters.az.value)"'
```

You can also preview the parameters that being used during a build in `Setup` -> `sd-setup-init` step

Pipeline Preview Screenshot:

![image](https://user-images.githubusercontent.com/15989893/67988338-e5564280-fbec-11e9-9946-93fa7d79de94.png)

![image](https://user-images.githubusercontent.com/15989893/67988423-251d2a00-fbed-11e9-8fe0-5644242d80b7.png)

## Further Reading

Please see [Screwdriver](http://screwdriver.cd)'s issue [1339](https://github.com/screwdriver-cd/screwdriver/issues/1339) for more discussions. Feel free to reach out at slack or submit github issues if you have any questions, thanks!