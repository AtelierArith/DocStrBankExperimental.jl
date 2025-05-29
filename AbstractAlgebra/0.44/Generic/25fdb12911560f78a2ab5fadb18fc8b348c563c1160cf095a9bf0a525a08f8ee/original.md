```
set_precision!(a::AbsMSeries, prec::Vector{Int})
```

Set the precisions of the variables in the given series to the values in the vector `prec`. The precisions must be non-negative. The series will be truncated to the new precisions. The mutated series is returned.
