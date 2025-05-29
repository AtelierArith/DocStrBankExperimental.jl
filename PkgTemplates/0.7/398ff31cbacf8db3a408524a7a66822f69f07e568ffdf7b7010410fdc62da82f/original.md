```
Readme(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/README.md",
    destination="README.md",
    inline_badges=false,
)
```

Creates a `README` file that contains badges for other included plugins.

## Keyword Arguments

  * `file::AbstractString`: Template file for the `README`.
  * `destination::AbstractString`: File destination, relative to the repository root. For example, values of `"README"` or `"README.rst"` might be desired.
  * `inline_badges::Bool`: Whether or not to put the badges on the same line as the package name.
  * `badge_order::Vector{typeof(Plugin)}`: Plugins in the order their badges should appear.
  * `badge_off::Vector{typeof(Plugin)}`: Plugins which should not have their badges added.
