```
RegistrySpec(name::String)
RegistrySpec(; name, url, path)
```

A `RegistrySpec` is a representation of a registry with various metadata, much like [`PackageSpec`](@ref).

Most registry functions in Pkg take a `Vector` of `RegistrySpec` and do the operation on all the registries in the vector.

# Examples

Below is a comparison between the REPL mode and the functional API::

| `REPL`               | `API`                                             |
|:-------------------- |:------------------------------------------------- |
| `MyRegistry`         | `RegistrySpec("MyRegistry")`                      |
| `MyRegistry=a67d...` | `RegistrySpec(name="MyRegistry", uuid="a67d...")` |
| `local/path`         | `RegistrySpec(path="local/path")`                 |
| `www.myregistry.com` | `RegistrySpec(url="www.myregistry.com")`          |
