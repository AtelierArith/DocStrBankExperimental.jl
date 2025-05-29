```
bezigon(corners::Vector{Point}, sides;
    close = false,
    action = :none))
```

Construct a bezigon, a path made of Bezier curves.

`corners` is an array of points, the corners of the bezigon, eg this triangle:

```julia
[Point(0, 0), Point(50, 50), Point(100, 0)]
```

`sides` is an array of arrays of points, where each array contains two control points, eg:

```julia
sides = [
    [Point(-10, -20), Point(40, -120)], # control points for first side
    [Point(120, -120), Point(180, -20)],
]
```

The first pair of `sides` (two points) are control points, which combine with the first two points in corners to define a Bezier curve. And so on for the next pair.

Returns a path.
