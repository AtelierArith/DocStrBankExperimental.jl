```
BBox(pmin::Vec, pmax::Vec)
```

Build an axis-aligned bounding box given the vector of minimum (`pmin`) and maximum (`pmax`) coordinates.

# Arguments

  * `pmin`: The minimum coordinates of the bounding box.
  * `pmax`: The maximum coordinates of the bounding box.

# Examples

```jldoctest
julia> p0 = Vec(0.0, 0.0, 0.0);

julia> p1 = Vec(1.0, 1.0, 1.0);

julia> box = BBox(p0, p1);
```
