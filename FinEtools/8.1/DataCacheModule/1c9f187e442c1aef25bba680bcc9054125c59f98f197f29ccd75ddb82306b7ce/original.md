```
(c::DataCache)(
    XYZ::AbstractVecOrMat{<:Real},
    tangents::AbstractMatrix{<:Real},
    feid::IT,
    qpid::IT,
) where {IT<:Integer}
```

Update the cache and retrieve the array.
