```
isinside(p::Point, pointlist::Vector{Point}
    allowonedge = false)
```

Is a point `p` inside a polygon `pointlist`?

If `allowonedge` is false, a point lying on the polygon is not inside.

Returns true if it does, or false.
