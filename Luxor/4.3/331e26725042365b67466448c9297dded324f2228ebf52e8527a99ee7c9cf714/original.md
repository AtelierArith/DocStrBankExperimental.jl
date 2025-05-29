```
slope(pointA::Point, pointB::Point)
```

Find angle of a line starting at `pointA` and ending at `pointB`.

Return a value between 0 and 2pi. Value will be relative to the current axes.

```julia
julia> slope(O, Point(0, 100)) |> rad2deg # y is positive down the page
90.0

julia> slope(Point(0, 100), O) |> rad2deg
270.0
```

The slope isn't the same as the gradient. A vertical line going up has a slope of 3π/2.
