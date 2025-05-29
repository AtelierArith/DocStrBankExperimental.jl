```
zeta_log_residue(O::AbsSimpleNumFieldOrder, error::Float64) -> ArbFieldElem
```

Computes the residue of the zeta function of $\mathcal O$ at $1$. The output will be an element of type `ArbFieldElem` with radius less then `error`.
