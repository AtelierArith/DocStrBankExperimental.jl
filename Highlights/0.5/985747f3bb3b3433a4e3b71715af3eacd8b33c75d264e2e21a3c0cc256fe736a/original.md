Generate a "stylesheet" for the given theme.

```julia
stylesheet(io, mime)
stylesheet(io, mime, theme)

```

Prints out the style information needed to colourise source code in the given `theme`. Note that `theme` defaults to `Themes.DefaultTheme`. Output is printed to `io` in the format `mime`. `mine` can be one of

  * `MIME("text/html")`
  * `MIME("text/css")`
  * `MIME("text/latex")`

# Examples

```jldoctest
julia> using Highlights

julia> buf = IOBuffer();

julia> stylesheet(buf, MIME("text/css"), Themes.EmacsTheme)

```
