```
fractional_ideal(O::AbsNumFieldOrder, M::ZZMatrix, b::ZZRingElem; M_in_hnf::Bool = false) -> AbsNumFieldOrderFractionalIdeal
```

Creates the fractional ideal of $\mathcal O$ with basis matrix $M/b$. If `M_in_hnf` is set, then it is assumed that $A$ is already in lower left HNF.
