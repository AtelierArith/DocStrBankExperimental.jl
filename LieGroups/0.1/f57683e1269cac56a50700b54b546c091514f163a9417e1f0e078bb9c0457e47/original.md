```
lie_bracket(::LieAlgebra{𝔽,MatrixMultiplicationGroupOperation}, X, Y)
lie_bracket!(::LieAlgebra{𝔽,MatrixMultiplicationGroupOperation}, Z, X, Y)
```

Compute the Lie bracket $[⋅,⋅]: \mathfrak g×\mathfrak g → \mathfrak g$, which for the for the [`MatrixMultiplicationGroupOperation`](@ref) yields the commutator bracket

$$
[X, Y] = XY-YX
$$

The computation can be done in-place of `Z`.
