```
SVGJS([output::Union{IO,AbstractString}], width=√200cm, height=10cm, jsmode=:embed) -> Backend
```

Create a Scalable Vector Graphic backend that enables Gadfly's interactivity (pan, zoom, etc.).  The default `jsmode` splices the requisite javascript directly into the output.  One can alternatively link to identical external javascript with `:linkabs` and `:linkrel`.  The output is normally passed to [`draw`](@ref).  Specify a filename using a string as the first argument.  See also [`SVG`](@ref).
