```
ideal(O::AbsSimpleNumFieldOrder, M::ZZMatrix; check::Bool = false, M_in_hnf::Bool = false) -> AbsNumFieldOrderIdeal
```

Creates the ideal of $\mathcal O$ with basis matrix $M$. If `check` is set, then it is checked whether $M$ defines an ideal (expensive). If `M_in_hnf` is set, then it is assumed that $M$ is already in lower left HNF.
