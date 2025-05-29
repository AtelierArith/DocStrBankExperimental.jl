```
quadratic_fast_bounder(fT::TaylorModelN)
```

Compute a *tighter* polynomial bound by the quadratic fast bounder. The returned bound corresponds to the "improved" polynomial bound with the remainder of the `TaylorModelN` included. This "improved" bound can be one of the following two:     1) An improved bound: if the domain of `fT` has a local minimizer,        then an improved bound is returned.     2) Original TaylorModel bound: if the local minimizer criteria is not        satisfied, then the original bound of `fT` is returned.

This algorithm is a slight modification to the Makino & Berz algorithm. For this algorithm the linear part is bounded by solving a simple set of linear equations (compared to the iterative procedure by Makino & Berz).
