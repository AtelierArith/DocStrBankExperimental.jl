```
placeeps(epsfile; log=false)
```

This function loads and interprets an EPS file previously exported by Cairo. Commands are 'applied' to the current drawing.

The primary intention is to extract some geometry  - points and curves, etc. - from an EPS vector graphic.

!!! warning
    This function reads only 'Cairo-flavoured' EPS files. Every application that exports EPS files defines its own chosen set of PostScript functions in a prolog. There's no standard. The 'Cairo-flavoured' EPS prolog is hard-coded into EPS files exported from Cairo so it's predictable, but other EPS exporters define their own flavour, defining and calling who knows what PostScript functions. So it's unlikely that EPS files from other sources will be successfully processed with this function.


Also note:

  * ignores clipping for now; I'm not sure how the Cairo->EPS->Cairo transformations work yet
  * ignores `rectfill`` commands for now - I think these are often used just for the initial BoundingBoxes/clipping, but if they're used matrix transforms they'll need interpreting somehow
  * ignores blends and gradients, embedded images, embedded fonts, among many other things...

Use `log` to print the commands to the REPL as well as execute them.

## Examples

```julia
@draw begin
    translate(boxtopleft())
    Luxor.placeeps("/tmp/julia.eps")
end
```

You can convert an SVG file to EPS by reading the SVG into Luxor, saving as EPS, then placing that saved EPS file onto a new drawing:

```julia
svgfile = readsvg("julia.svg")
@eps begin
    placeimage(svgfile, centered = true)
end 800 500 "/tmp/julia.eps"
@draw begin
    translate(boxtopleft())
    placeeps("/tmp/julia.eps")
end
```

If you want to put the list of Luxor commands in a text file for pasting into another file, you could try this (Julia v.1.7 and up). Let's say you have an SVG called `julia.svg`.

```julia
# load an SVG and save as EPS
@eps begin
    svgf = readsvg("julia.svg")
    placeimage(svgf, centered = true)
end 500 500 "/tmp/t.eps"

# convert EPS to Luxor commands
redirect_stdio(stdout = "/tmp/output.jl") do
    placeeps("/tmp/t.eps", log = true)
end

# include Luxor commands and save as a new SVG:
@svg begin
    translate(boxtopleft())
    include("/tmp/output.jl")
end 500 500 "/tmp/julia.svg"
```
