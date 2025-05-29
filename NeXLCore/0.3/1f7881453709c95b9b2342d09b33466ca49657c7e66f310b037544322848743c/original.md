The MonteCarlo uses the shapes defined in GeometryBasics basics as the foundation for its  sample construction mechanisms.  However, GeometryBasics basics does not provide all the  necessary methods.  Three additional methods are 

```
isinside(r::Shape, pos::Position)
```

Is `pos` strictly inside `r`?

```
intersection(r::Shape, pos0::Particle, pos1::Particle)::Float64
```

Return a number `f` which represent the fraction of the distance from `pos0` to `pos1` that first intersects the `Shape` `r`.  The intersection point will equal `pos0 .+ f*(pos1 .- pos0)`. If `f` is between 0.0 and 1.0 then the intersection is on the interval between `pos0` and `pos1`. If the ray from `pos0` towards `pos2` does not intersect `r` then this function returns Inf64.
