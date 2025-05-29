```
lie_bracket!(𝔤::LieAlgebra{𝔽,AdditionGroupOperation}, X, Y)
lie_bracket!(𝔤::LieAlgebra{𝔽,AdditionGroupOperation}, Z, X, Y)
```

Compute the Lie bracket $[⋅,⋅]: \mathfrak g×\mathfrak g → \mathfrak g$, which for the for the [`AdditionGroupOperation`](@ref) simplifies to the corresponding [`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`). The computation can be done in-place of `Z`.
