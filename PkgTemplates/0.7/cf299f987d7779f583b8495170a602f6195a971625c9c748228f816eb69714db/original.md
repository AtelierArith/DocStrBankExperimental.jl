```
Formatter(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/.JuliaFormatter.toml",
    style="nostyle"
)
```

Create a `.JuliaFormatter.toml` file, used by [JuliaFormatter.jl](https://github.com/domluna/JuliaFormatter.jl) and the Julia VSCode extension to configure automatic code formatting.

This file can be entirely customized by the user, see the [JuliaFormatter.jl docs](https://domluna.github.io/JuliaFormatter.jl/stable/).

## Keyword Arguments

  * `file::String`: Template file for `.JuliaFormatter.toml`.
  * `style::String`: Style name, defaults to `"nostyle"` for an empty style but can also be one of `("sciml", "blue", "yas")` for a fully preconfigured style.
