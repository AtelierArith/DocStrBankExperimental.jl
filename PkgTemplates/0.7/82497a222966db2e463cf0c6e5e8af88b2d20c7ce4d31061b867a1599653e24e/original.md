```
License(; name="MIT", path=nothing, destination="LICENSE")
```

Creates a license file.

## Keyword Arguments

  * `name::AbstractString`: Name of a license supported by PkgTemplates. Available licenses can be seen [here](https://github.com/JuliaCI/PkgTemplates.jl/tree/master/templates/licenses).
  * `path::Union{AbstractString, Nothing}`: Path to a custom license file. This keyword takes priority over `name`.
  * `destination::AbstractString`: File destination, relative to the repository root. For example, `"LICENSE.md"` might be desired.
