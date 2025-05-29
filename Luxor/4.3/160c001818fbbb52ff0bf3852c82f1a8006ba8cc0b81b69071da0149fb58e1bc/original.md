```
polysample(p::Vector{Point}, npoints::T where T <: Integer;
        closed=true)
```

Sample the polygon `p`, returning a polygon with `npoints` to represent it. The first sampled point is:

```1/`npoints` * `perimeter of p````

away from the original first point of `p`.

If `npoints` is the same as `length(p)` the returned polygon is the same as the original, but the first point finishes up at the end (so `new=circshift(old, 1)`).

If `closed` is true, the entire polygon (including the edge joining the last point to the first point) is sampled.

If `include_first` is true, the first point of `plist` is included in the result.

If the resulting polygon's first and end points are the same, the end point is discarded.
