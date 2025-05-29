```
fractional_ideal(O::RelNumFieldOrder, M::PMat; M_in_hnf::Bool = false) -> RelNumFieldOrderFractionalIdeal
```

Creates the fractional ideal of $\mathcal O$ with basis pseudo-matrix $M$. If `M_in_hnf` is set, then it is assumed that $M$ is already in lower left pseudo HNF.
