This macro is equivalent to [`@frompackage`](@ref) but assumes the calling file as the `target` argument. So the code 

```
@fromparent import_block
```

is equivalent to

```
@frompackage @__FILE__ import_block
```

Refer to the [`@frompackage`](@ref) docstring and the package [documentation](https://disberd.github.io/PlutoDevMacros.jl/dev/frompackage/introduction/#Introduction) for understanding its use. See also: [`@addmethod`](@ref)
