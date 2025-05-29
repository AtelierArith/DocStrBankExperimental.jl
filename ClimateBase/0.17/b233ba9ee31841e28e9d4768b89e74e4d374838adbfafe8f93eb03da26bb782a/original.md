```
uniquelats(A::ClimArray) → idxs, lats
uniquelats(c::Vector{<:AbstractVector}) → idxs, lats
```

Find the unique latitudes of `A`. Return the indices (vector of ranges) that each latitude in `lats` covers, as well as the latitudes themselves.
