```
CoherencyMatrix(e11, e21, e12, e22, basis::NTuple{2, PolBasis})
```

Constructs the coherency matrix with components    e11 e12    e21 e22 relative to the tensor product basis, `|basis[1]><basis[2]|`. Note that basis[1] and basis[2] could be different.

For instance

```julia
c = Coherency(1.0, 0.0, 0.0, 1.0, CirBasis(), LinBasis())
```

elements correspond to     RX* RY*     LX* LY*
