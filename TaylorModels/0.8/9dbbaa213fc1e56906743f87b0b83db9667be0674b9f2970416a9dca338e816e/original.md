```
linear_dominated_bounder(fT::TaylorModelN, ϵ=1e-3::Float64, max_iter=5::Int)
```

Compute a tighter polynomial bound for the Taylor model `fT` by the linear dominated bounder algorithm. The linear dominated algorithm is applied until the bound of `fT` gets tighter than `ϵ` or the number of steps reachs `max_iter`. The returned bound corresponds to the improved polynomial bound with the remainder of the `TaylorModelN` included.
