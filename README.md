# Lix cache [![Nightly builds](https://github.com/xaltsc/lix-nightly/actions/workflows/nightly.yaml/badge.svg)](https://github.com/xaltsc/lix-nightly/actions/workflows/nightly.yaml) [![Watch nixpkgs updates](https://github.com/xaltsc/lix-nightly/actions/workflows/watch-nixpkgs.yaml/badge.svg)](https://github.com/xaltsc/lix-nightly/actions/workflows/watch-nixpkgs.yaml)
The only purpose of this repo is to provide daily caches of upstream [Lix](https://lix.systems).

New builds happen on two events:
- Each day, it checks for updates from Lix repo, and builds it
- Every hour or so, it checks for updates from `nixos-unstable`. If it has been updated, new builds happen.

The cache is available at
[`https://xaltsc-lix.cachix.org`](https://xaltsc-lix.cachix.org),
its public key is `xaltsc-lix.cachix.org-1:jUJOx2iEEQJi34ACTQR4Nz24wOQciGvsPuiYQCZPzrc=`.

This fits the use case where you just run `nix flake update` to update all inputs, as the packages
are built using the latest version of `nixos-unstable`.

This repo acts like a `nightly` tag for Lix.
In order to use it, point your `lix-module` input to this repo `github:xaltsc/lix-nightly` to be
sure to use a nightly cached version. You shouldn't follow upstream `lix` as this is pinned nightly
as well in the repo, however, you should follow `nixpkgs`. Unless you are unlucky (or don't use `nixos-unstable`),
versions will match and this will not cause local rebuilds.

This flake reexposes everything the upstream [`lix-project/nixos-module`](https://git.lix.systems/lix-project/nixos-module) exposes.

A [`weekly`](https://github.com/xaltsc/lix-nightly/releases/tag/weekly) tag is available for those
who want less nightly builds. Builds from this commit are pinned on cachix for a week.
