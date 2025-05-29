```
fp_rpa(tm::TaylorModel1{Interval{T},T})
fp_rpa(tm::RTaylorModel1{Interval{T},T})
```

Convert a `tm` TaylorModel1 to a TaylorModel1 whose polynomial coefficients are `Float64`. The accumulated error is added to the remainder. The mid point of the expansion interval is preferentially rounded down if it is not an exactly representable value.
