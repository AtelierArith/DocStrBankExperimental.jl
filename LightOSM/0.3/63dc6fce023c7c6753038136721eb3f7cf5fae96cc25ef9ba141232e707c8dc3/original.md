```
heading(a::GeoLocation, b::GeoLocation, return_units::Symbol=:degrees)
heading(a::Node, b::Node, return_units::Symbol=:degrees)
heading(A::Vector{GeoLocation}, B::Vector{GeoLocation}, return_units::Symbol=:degrees)
heading(A::Vector{Node}, B::Vector{Node}, return_units::Symbol=:degrees)
```

Calculates heading(s) / bearing(s) between two points (`a` is origin, `b` is destination) or two vectors of points (`A` is vector of origins, `B` is vector of destinations). Points can be either `GeoLocation`s or `Node`s.

Depending on the `return_units` chosen, the return angle is in range of [-π, π] if `:radians` or [-180, 180] if `:degrees`. Additionally, adjusts destination longitude in case the straight line path between a and b crosses the International Date Line.
