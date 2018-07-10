# Release

[![Parcel](docs/parcel.png)](https://pixabay.com/en/box-surprise-explosion-packet-307087/)

[![Release](https://img.shields.io/github/release/whiskeysierra/release.svg)](https://github.com/whiskeysierra/release/releases)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/whiskeysierra/release/master/LICENSE)

Makes releasing maven-based open-source projects easy and fun.

- **Technology stack**: Git, Maven, semantic versioning
- **Status**:  1.x, used in production

## Example

```bash
./release.sh patch
```

## Features

- Supports semver semantics
- Manages versions in Maven POMs
- Supports multi-module builds
- Deploys to remote maven repository
- Tags versions in Git
- Supports pre-releases

## Dependencies

- [Maven 3](https://maven.apache.org/)
- [Maven wrapper](https://github.com/takari/maven-wrapper)
- [Git](https://git-scm.com/)
- [semver](https://github.com/npm/node-semver), optional see [Alternative](#without-semver)

## Installation

```bash
wget https://raw.githubusercontent.com/whiskeysierra/release/master/release.sh
git add release.sh
git commit -m "Added release script"
```

## Configuration

Specify your SCM URL in your parent POM:

```xml
<scm>
    <connection>scm:git:git@github.com:org/repo.git</connection>
</scm>
```

## Usage

### Major, minor and patch versions

```bash
./release.sh minor
```

### Pre-release versions

Assuming your latest tag is `1.8.1` and the intent is to deploy a release candidate `2.0.0-RC.0`:

```bash
./release premajor
```

Any subsequent pre-releases can be deployed with:

```bash
./release.sh prerelease
```

### Without semver

If the `semver` dependency is undesired, then the script can easily be modified so that it takes
the release and next development version as arguments:

```bash
: ${2?"Usage: $0 <release-version> <next-version>"}

release=$1
next=$2
```

The script can then be used like this:

```bash
./release 2.0.0-RC.0 2.0.0-SNAPSHOT
```

## Getting Help

If you have questions, concerns, bug reports, etc., please file an issue in this repository's [Issue Tracker](../../issues).

## Getting Involved/Contributing

To contribute, simply make a pull request and add a brief description (1-2 sentences) of your addition or change. For
more details, check the [contribution guidelines](CONTRIBUTING.md).

## Alternatives

- [Maven Release Plugin](http://maven.apache.org/maven-release/maven-release-plugin/)

## References

- [Maven Release Plugin: The Final Nail in the Coffin](https://axelfontaine.com/blog/final-nail.html)

