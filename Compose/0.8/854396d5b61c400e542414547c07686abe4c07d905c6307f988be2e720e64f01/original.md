```
SVG([output::Union{IO,AbstractString}], width=√200cm, height=10cm, jsmode=:none) -> Backend
```

Create a Scalable Vector Graphic backend.  The output is normally passed to [`draw`](@ref).  Specify a filename using a string as the first argument. `jsmode` can be one of `:none`, `:embed`, `:linkabs`, or `:linkrel`.  See also [`SVGJS`](@ref).

# Examples

```
c = compose(context(), line())
draw(SVG("myplot.svg"), c)
```
