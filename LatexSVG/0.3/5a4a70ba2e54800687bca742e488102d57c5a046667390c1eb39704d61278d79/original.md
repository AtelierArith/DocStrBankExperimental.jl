```
config!(; texengine=nothing, preamble=nothing, export_prefs=false)
```

Configure persistent settings for the LaTeX engine and the preamble:

  * `texengine` can be [`XeLaTeX`](@ref), [`PDFLaTeX`](@ref), or [`LuaLaTeX`](@ref)
  * `preamble` can be an `AbstractString` or a `Vector` of `AbstractString`s.

Two examples:

```julia-repl
julia> config!(texengine=PDFLaTeX)
```

This sets the default LaTeX engine to be `PDFLaTeX` *for all future sessions*.

```julia-repl
julia> config!(preamble=["\usepackage{mathtools}", "\usepackage{xcolor}"])
```

This sets the default preamble to be

```latex
\usepackage{mathtools}
\usepackage{xcolor}
```

*for all future sessions*, replacing the original default of

```latex
\usepackage{amsmath,amsthm,amssymb}
\usepackage{color}
```

You can also call `config!()` without any keyword argument. In this case your current LaTeX engine and preamble will be stored as the default.

These preferences are stored in a `LocalPreferences.toml` file in your active project. If `export_prefs=true`, they will instead be written into your `Project.toml`. Either way, if you have multiple projects using this package you need to set the preference for them individually.
