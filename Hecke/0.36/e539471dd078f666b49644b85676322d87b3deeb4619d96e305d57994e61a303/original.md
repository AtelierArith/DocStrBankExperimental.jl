```
picard_group(O::AlgAssAbsOrd, prepare_ref_disc_log::Bool = false)
  -> FinGenAbGroup, MapPicardGroup
```

Given an order $O$ in a commutative algebra over $\mathbb Q$, this function returns the picard group of $O$. If `prepare_ref_disc_log` is `true`, then (possibly expensive) preparations for the computation of refined discrete logarithms in non maximal orders are done.
