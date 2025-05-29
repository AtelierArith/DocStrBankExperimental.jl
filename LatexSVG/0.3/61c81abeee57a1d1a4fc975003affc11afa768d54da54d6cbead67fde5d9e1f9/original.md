```
latexsvg(latex::AbstractString, engine=texengine(); standalone=false, extra_args=[])
```

Renders `latex` as an SVG string. `latex` is the LaTeX code that you want to render, `engine` is the LaTeX engine to use and defaults to the one currently in use for this session. You can change the engine for this session with [`texengine!`](@ref), or set the default permanently with [`config!`](@ref).

The output can be configured with a few keyword arguments:

  * If `standalone=true`, it is assumed that `latex` is a complete document, thus the preamble will be ignored. Otherwise (and this is the default) `latex` will be inserted into a LaTeX document, whose preamble can be configured with [`add_preamble!`](@ref) and reset with [`reset_preamble!`](@ref). You can get the current complete preamble with [`preamble`](@ref).
  * `extra_args` allows you to pass additional commandline flags/arguments to the LaTeX engine. For instance, if your LaTeX code contains `minted` code blocks (for some reason), you would need to set `extra_args=["--shell-escape"]`.
