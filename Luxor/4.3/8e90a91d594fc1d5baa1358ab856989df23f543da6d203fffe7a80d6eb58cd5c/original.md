```
arrow(start::Point, C1::Point, C2::Point, finish::Point, action=:stroke;
    linewidth       = 1.0,
    arrowheadlength = 10,
    arrowheadangle  = pi/8,
    startarrow      = false,
    finisharrow     = true,
    decoration      = 0.5,
    decorate        = nothing
    arrowheadfunction = nothing)
```

Draw a Bezier curved arrow, from `start` to `finish`, with control points `C1` and `C2`. Arrow heads can be added/hidden by changing `startarrow` and `finisharrow` options.

The `decorate` keyword argument accepts a function that can execute code at one or more locations on the arrow's shaft. The inherited graphic environment is centered at each point on the shaft given by scalar or vector `decoration`, and the x-axis is aligned with the direction of the curve at that point.

### Example

This code draws an arrow head that's filled with orange and outlined in green.

```julia
function myarrowheadfunction(originalendpoint, newendpoint, shaftangle)
    @layer begin
        setline(5)
        translate(newendpoint)
        rotate(shaftangle)
        sethue("orange")
        ngon(O, 20, 3, 0, :fill)
        sethue("green")
        ngon(O, 20, 3, 0, :stroke)
    end
end

@drawsvg begin
    background("white")
    arrow(O, 220, 0, π,
        linewidth=10,
        arrowheadlength=30,
        arrowheadangle=π/7,
        clockwise=true,
        arrowheadfunction = myarrowheadfunction)
end
```
