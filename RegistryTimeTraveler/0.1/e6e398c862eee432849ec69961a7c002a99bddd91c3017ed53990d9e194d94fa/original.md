```julia
clone_registries_for_package(
    pkg::PackageSpec;
    registries_dir::AbstractString=get_registries_dir(),
    registries::Vector{Pkg.Registry.RegistryInstance} = Pkg.Registry.reachable_registries(),
)::Vector{Pkg.Registry.RegistryInstance}
```

For a specified package version, this will look at what date it was released in its corresponding registry. Then it will clone all registries at that specified date.

You can then install packages as if you traveled back in time to the package release date.

Note: it will clone each registry twice, to try to reduce the download size.

  * Once to get only the registry GIT history and find the right commit.
  * And a second time to only clone the registry at that commit.

At the time of writing this still downloads about 220 MB of the General registry.

# Example

```julia
using Pkg, RegistryTimeTraveler

# go to some folder where registries will be installed
cd(pwd())

# choose your package and version
pkg = PackageSpec(name="JSON3", version="1.9.3")

cloned_registries = clone_registries_for_package(pkg)

# very important: dont let Pkg update the cloned registries!
Pkg.OFFLINE_MODE[] = true

Pkg.activate(".")
Pkg.add(pkg.name; registries=cloned_registries, preserve=Pkg.PRESERVE_NONE)

```
