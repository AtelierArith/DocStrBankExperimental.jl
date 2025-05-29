FeatureRegistries.jl is a Julia package to create registries of a package’s features, letting package users discover and use them more easily. FeatureRegistries.jl lets you create tables that list package features so that

  * users can explore and discover features,
  * users can search features through a consistent interface; and
  * developers of third-party packages can transparently add functionality

## Usage

### Package users

Package users of packages can use registries through:

  * [`find`](#)/`filter`/`findfirst` to subset the list of features based on filters,
  * [`info`](#)`(registry)` to get more information on a specific registry,
  * `registry[id]` to inspect an entry in a registry,
  * [`load`](#)`(registry)` to access a feature

See also [how to use registries](/documents/docs/using.md).

### Package developers

Developers can create registries using [`Registry`](#) and [`Field`](#), `push!(registry)`.
