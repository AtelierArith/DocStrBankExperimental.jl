```
as(Array, [transformation], dims...)
as(Array, [transformation], dims)
```

Return a transformation that applies `transformation` (which defaults to `asℝ`, the identity transformation for scalars) repeatedly to create an array with the given `dims`.

`Matrix` or `Vector` can be used in place of `Array`, with conforming dimensions.

# Example

```julia
as(Array, asℝ₊, 2, 3)           # transform to a 2x3 matrix of positive numbers
as(Vector, 3)                   # ℝ³ → ℝ³, identity
```
