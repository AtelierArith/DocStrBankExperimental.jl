```
lie_bracket!(𝔤::LieAlgebra, X, Y)
lie_bracket!(𝔤::LieAlgebra, Z, X, Y)
```

Compute the Lie bracket $[⋅,⋅]: \mathfrak g×\mathfrak g → \mathfrak g$ which fulfills

1. $[X,X] = 0$ for all $X ∈ \mathfrak g$
2. The Jacobi identity $[X, [Y,Z]] = [[X,Y],Z] = [Y, [X,Z]]$ holds for all $X, Y, Z ∈ \mathfrak g$.

The computation can be done in-place of `Z`.
