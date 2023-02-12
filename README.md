# gha-setup-yq <a href="https://github.com/vegardit/gha-setup-yq/" title="GitHub Repo"><img height="30" src="https://raw.githubusercontent.com/simple-icons/simple-icons/develop/icons/github.svg?sanitize=true"></a>

[![Build](https://github.com/vegardit/gha-setup-yq/actions/workflows/build.yml/badge.svg)](https://github.com/vegardit/gha-setup-yq/actions/workflows/build.yml)
[![License](https://img.shields.io/github/license/vegardit/gha-setup-yq.svg?label=license)](#license)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-v2.0%20adopted-ff69b4.svg)](CODE_OF_CONDUCT.md)


**Feedback and high-quality pull requests are highly welcome!**

1. [What is it?](#what-is-it)
1. [Usage](#github_action)
1. [License](#license)


## <a name="what-is-it"></a>What is it?

**gha-setup-yq** is a GitHub action to install the [yq](https://github.com/mikefarah/yq/releases/) command-line YAML, JSON, XML, CSV and properties parser/processor.


## <a name="github_action"></a>Usage

In your GitHub actions workflow specify:

### Installing the latest version:
```yaml
name: Build
on: [ push, pull_request ]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Setup yq
      uses: vegardit/gha-setup-yq@v1

    - name: Use yq
      run: |
        yq --version
        echo 'greeting: "Hello World"' | yq -e ".greeting"
```

### Installing a specific version:

```yaml
name: Build
on: [ push, pull_request ]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Setup yq 4.30.6
      uses: vegardit/gha-setup-yq@v1
      with:
        use-cache: true
        version: 4.30.6

    - name: Use yq
      run: |
        yq --version
        echo 'greeting: "Hello World"' | yq -e ".greeting"
```

### Configuration parameters and default values

```yaml
with:
  version: any    # yq version to install, possible values:
                  # - "any" -> meaning if jq is installed already or found in cache, then just use that version
                  # - "latest"
                  # - a version number, e.g. '4.30.8'
  use-cache: true # if the downloaded yq binary should be cached using the GHA caching service
```


## <a name="license"></a>License

All files are released under the [Apache License 2.0](LICENSE.txt).

Individual files contain the following tag instead of the full license text:
```
SPDX-License-Identifier: Apache-2.0
```

This enables machine processing of license information based on the SPDX License Identifiers that are available here: https://spdx.org/licenses/.
