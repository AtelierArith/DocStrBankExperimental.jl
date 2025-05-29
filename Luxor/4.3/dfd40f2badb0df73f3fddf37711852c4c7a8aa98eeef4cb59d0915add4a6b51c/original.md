```
pointinverse(A::Point, centerpoint::Point, rad)
```

Find `A′`, the inverse of a point A with respect to a circle `centerpoint`/`rad`, such that:

```julia
distance(centerpoint, A) * distance(centerpoint, A′) == rad^2
```

Return (true, A′) or (false, A).
