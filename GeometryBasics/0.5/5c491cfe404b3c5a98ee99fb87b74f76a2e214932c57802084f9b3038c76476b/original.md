```
connect(points::AbstractVector{<: Point}, P::Type{<: Polytope{N}}, skip::Int = N)
```

Creates a view that connects a number of points to a Polytope `P`. Between each polytope, `skip` elements are skipped until the next starts. Example: ```julia x = connect(Point[(1, 2), (3, 4), (5, 6), (7, 8)], Line, 2) x == [Line(Point(1, 2), Point(3, 4)), Line(Point(5, 6), Point(7, 8))]
