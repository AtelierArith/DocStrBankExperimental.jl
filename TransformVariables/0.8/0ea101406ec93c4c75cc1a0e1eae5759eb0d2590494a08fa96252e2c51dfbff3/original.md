```
as(SArray{S}, [inner_transformation])
```

Return a transformation that applies `inner_transformation` (which defaults to `asℝ`, the identity transformation for scalars) repeatedly to create an array with the given dimensions.

`SMatrix` or `SVector` can be used in place of `SArray`, with conforming dimensions.

# Example

```julia
as(SArray{2,3}, asℝ₊, 2, 3)     # transform to a 2x3 SMatrix of positive numbers
as(SVector{3})                   # ℝ³ → ℝ³, identity, but an SVector
```
