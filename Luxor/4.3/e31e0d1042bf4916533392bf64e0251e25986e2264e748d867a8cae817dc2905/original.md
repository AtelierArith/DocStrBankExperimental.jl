```
setcolor("gold")
setcolor("darkturquoise")
```

Set the current color to a named color. This use the definitions in Colors.jl to convert a string to RGBA eg `setcolor("gold")` or "green", "darkturquoise", "lavender", etc. The list is at `Colors.color_names`.

Use `sethue()` for changing colors without changing current opacity level.

`sethue()` and `setcolor()` return the three or four values that were used:

```julia
julia> setcolor(sethue("red")..., .8)
(1.0N0f8, 0.0N0f8, 0.0N0f8, 0.8)

julia> sethue(setcolor("red")[1:3]...)
(1.0N0f8, 0.0N0f8, 0.0N0f8)
```

You can also do:

```
using Colors
sethue(colorant"red")
```

See also [`setcolor`](@ref).
