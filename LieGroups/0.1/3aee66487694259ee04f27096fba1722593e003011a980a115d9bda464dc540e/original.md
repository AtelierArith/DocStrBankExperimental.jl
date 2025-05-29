```
lie_bracket(::LieAlgebra{𝔽,AbelianMultiplicationGroupOperation}, X, Y)
lie_bracket!(::LieAlgebra{𝔽,AbelianMultiplicationGroupOperation}, Z, X, Y)
```

Compute the Lie bracket $[⋅,⋅]: \mathfrak g×\mathfrak g → \mathfrak g$, which for the for the [`AbelianMultiplicationGroupOperation`](@ref) yields the zero vector of the [`LieAlgebra`](@ref) due to commutativity. 

$$
[X, Y] = XY-YX = 0
$$

The computation can be done in-place of `Z` if `Z` is `mutable`.
