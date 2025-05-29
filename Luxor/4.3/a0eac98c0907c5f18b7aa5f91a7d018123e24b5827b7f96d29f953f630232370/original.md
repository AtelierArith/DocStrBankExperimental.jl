```
arrow(startpoint::Point, endpoint::Point;
    linewidth         = 1.0,
    arrowheadlength   = 10,
    arrowheadangle    = pi/8,
    decoration        = 0.5 or range(),
    decorate          = nothing,
    arrowheadfunction = nothing)
```

Draw a line between two points and add an arrowhead at the end. The arrowhead length will be the length of the side of the arrow's head, and the arrowhead angle is the angle between the sloping side of the arrowhead and the arrow's shaft.

Arrows don't use the current linewidth setting (`setline()`), and defaults to 1, but you can specify another value. It doesn't need stroking/filling, the shaft is stroked and the head filled with the current color.

### Decoration

The `decorate` keyword argument accepts a function with zero arguments that can execute code at one or more locations on the arrow's shaft. The inherited graphic environment is centered at each point on the shaft between 0 and 1 given by scalar or vector `decoration`, and the x-axis is aligned with the direction of the curve at that point.

### Arrowheads

A triangular arrowhead is drawn by default. But you can pass a function to the `arrowheadfunction` keyword argument that accepts three arguments: the shaft end, the arrow head end, and the shaft angle. Thsi allows you to draw any shape arrowhead.

### Example

```julia
function redbluearrow(shaftendpoint, endpoint, shaftangle)
    @layer begin
        sethue("red")
        sidept1 = shaftendpoint  + polar(10, shaftangle + π/2 )
        sidept2 = shaftendpoint  - polar(10, shaftangle + π/2)
        poly([sidept1, endpoint, sidept2], :fill)
        sethue("blue")
        poly([sidept1, endpoint, sidept2], :stroke, close=false)
    end
end

@drawsvg begin
    background("white")
    arrow(O, O + (120, 120),
        linewidth=4,
        arrowheadlength=40,
        arrowheadangle=π/7,
        arrowheadfunction = redbluearrow)

    arrow(O, 100, 3π/2, π,
        linewidth=4,
        arrowheadlength=20,
        clockwise=false,arrowheadfunction=redbluearrow)
end 800 250
```
