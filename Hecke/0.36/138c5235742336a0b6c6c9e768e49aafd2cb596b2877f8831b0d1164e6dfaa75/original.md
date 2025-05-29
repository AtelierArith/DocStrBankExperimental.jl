```
is_on_curve(C::HypellCrv{T}, coords::Vector{T}) -> Bool
```

Return true if `coords` defines a point on $C$ and false otherwise. The array `coords` must have length 2.
