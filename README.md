# `wolfi-openstack`

This repository contains [melange](https://github.com/chainguard-dev/melange) definitions for building
all of the OpenStack services.  This repository is used to build the packages that are used in the
lightweight Wolfi based images used by [Atmosphere](https://github.com/vexxhost/atmosphere).

## Usage

### Building a package

You can easily build a package by running the following command (for example, Barbican).  You will
need to have both the `make` and the `melange` tools installed.

```console
make package/py3-barbican
```

## FAQ

### Why is there non-OpenStack packages here?

This repository builds all of the Python dependencies needed which are pulled out of the OpenStack
[upper-constraints](https://github.com/openstack/requirements/blob/master/upper-constraints.txt) in mind,
which is not fast moving.

### Aren't some of those packages out of date?

Wolfi is great for it's continuously up-to-date packages, however, some of the packages may move ahead
of the ones needed by OpenStack, so we build them here all locally at an older version.

### Why can't we just use the latest versions of everything to avoid CVEs?

There is a lot of effort involved in being able to support a newer version of a dependency, since that
involves making changes that are not upstreamable (because upstream will not change their constraints).

> [!NOTE]
> Our customers who have support subscriptions get access to packages that our team works on backporting
> patches to in order to enable newer version of dependencies to eliminate any potential CVEs.
>
> If you're interested, please [contact us](https://vexxhost.com/contact-us/) for more information.

### What versions does this repository build?

At the moment, this repository is strictly focused on building *tagged* versions of the OpenStack services,
if you are looking for a fix that has not been released, we suggest asking upstream to tag a new release
and it will be built here automatically.

> [!NOTE]
> Our customers who have support subscriptions are able to file support tickets with any issues or requesting
> a backport of a fix to a package that is not yet tagged.  After our team vets the fix, we will backport it
> in the packages we make available to our customers.
>
> If you're interested, please [contact us](https://vexxhost.com/contact-us/) for more information.
