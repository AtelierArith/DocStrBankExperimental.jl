```
svgstring()
```

Return the current and recently completed SVG drawing as a string of SVG commands.

Returns `""` if there is no SVG information available.

To display the SVG string as a graphic, try the `HTML()` function in Base.

```julia
...
HTML(svgstring())
```

In a Pluto notebook, you can also display the SVG using:

```julia
# using PlutoUI
...
PlutoUI.Show(MIME"image/svg+xml"(), svgstring())
```

(This lets you right-click to save the SVG.)

## Example

This example examines the generated SVG code produced by drawing the Julia logo.

```julia-repl
julia> Drawing(500, 500, :svg)

julia> origin()

julia> julialogo()

julia> finish()

julia> s = svgstring()

julia> eachmatch(r"rgb.*?;", s) |> collect
6-element Vector{RegexMatch}:
 RegexMatch("rgb(100%,100%,100%);")
 RegexMatch("rgb(0%,0%,0%);")
 RegexMatch("rgb(79.6%,23.5%,20%);")
 RegexMatch("rgb(25.1%,38.8%,84.7%);")
 RegexMatch("rgb(58.4%,34.5%,69.8%);")
 RegexMatch("rgb(22%,59.6%,14.9%);")
```

Here's another example, post-processing the SVG file with the `svgo` optimizer.

```julia
@drawsvg begin
    background("midnightblue")
    fontface("JuliaMono-Regular")
    fontsize(20)
    sethue("gold")
    text("JuliaMono: a monospaced font ", halign=:center)
    text("with reasonable Unicode support", O + (0, 22), halign=:center)
end 500 150
write("txt.svg", svgstring())
# minimize SVG
run(`svgo txt.svg -o txt-min.svg`)
```
