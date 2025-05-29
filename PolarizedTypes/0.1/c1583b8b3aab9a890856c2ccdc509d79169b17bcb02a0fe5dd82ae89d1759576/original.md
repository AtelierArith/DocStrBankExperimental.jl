```
CoherencyMatrix(e11, e21, e12, e22, basis::PolBasis)
```

Constructs the coherency matrix with components    e11 e12    e21 e22 relative to the tensor product basis, `basis` given by `|basis><basis|`.

For instance

```julia
c = Coherency(1.0, 0.0, 0.0, 1.0, CirBasis())
```

elements correspond to     RR* RL*     LR* LL*
