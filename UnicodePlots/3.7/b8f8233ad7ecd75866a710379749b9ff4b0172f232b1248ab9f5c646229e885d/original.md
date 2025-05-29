```
savefig(p, filename; color = false, kw...)
```

Save the given plot to a `txt or`png` file.

# Arguments - `txt`

  * `color::Bool = false`: output the ANSI color codes to the file.

# Arguments - `png`

see help?> UnicodePlots.png_image

# Examples

```julia-repl
julia> savefig(lineplot([0, 1]), "foo.txt")
julia> savefig(lineplot([0, 1]), "foo.png"; font = "JuliaMono", pixelsize = 32, transparent = false)
```
