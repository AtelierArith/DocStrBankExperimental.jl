```
distance_transform(F::AbstractArray{CartesianIndex}, [w=nothing]) -> D
```

Compute the distance transform of `F`, where each element `F[i]` represents a "target" or "feature" location assigned to `i`. Specifically, `D[i]` is the distance between `i` and `F[i]`. Optionally specify the weight `w` assigned to each coordinate; the default value of `nothing` is equivalent to `w=(1,1,...)`.

See also: [`feature_transform`](@ref).
