```
repartition!(tdst::AbstractTensorMap{S}, tsrc::AbstractTensorMap{S}) where {S} -> tdst
```

Write into `tdst` the result of repartitioning the indices of `tsrc`. This is just a special case of a transposition that only changes the number of in- and outgoing indices.

See [`repartition`](@ref) for creating a new tensor.
