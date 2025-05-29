```
ideal(O::RelNumFieldOrder, M::PMat; check::Bool = true, M_in_hnf::Bool = false) -> RelNumFieldOrderIdeal
```

Creates the ideal of $\mathcal O$ with basis pseudo-matrix $M$. If `check` is set, then it is checked whether $M$ defines an ideal. If `M_in_hnf` is set, then it is assumed that $M$ is already in lower left pseudo HNF.
