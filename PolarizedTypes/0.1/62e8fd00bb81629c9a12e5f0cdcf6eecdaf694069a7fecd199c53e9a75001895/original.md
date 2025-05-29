```
CoherencyMatrix(e11, e21, e12, e22, basis1::PolBasis basis2::PolBasis)
```

Constructs the coherency matrix with components    e11 e12    e21 e22 relative to the tensor product basis, `basis` given by `|basis1><basis2|`.

For instance

```julia
c = Coherency(1.0, 0.0, 0.0, 1.0, CirBasis(), LinBasis())
```

elements correspond to     RX* RY*     LX* LY*
