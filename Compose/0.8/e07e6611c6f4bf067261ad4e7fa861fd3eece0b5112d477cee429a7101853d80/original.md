```
PNG([output::Union{AbstractString, IO}], width=√200cm, height=10cm; dpi=96) -> Backend
```

Create a Portable Network Graphics backend. The output is normally passed to [`draw`](@ref). Specify a filename using a string as the first argument.  Depends on `Cairo.jl`.

# Examples

```
using Cairo
c = compose(context(), circle())
draw(PNG("myplot.png", 10cm, 5cm, dpi=250), c)
```
