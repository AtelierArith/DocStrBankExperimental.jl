```
TimeDependentSum(lazysum, coeffs, init_time)
TimeDependentSum(::Type{Tf}, basis_l, basis_r; init_time=0.0)
TimeDependentSum([::Type{Tf},] [basis_l,] [basis_r,] coeffs, operators; init_time=0.0)
TimeDependentSum([::Type{Tf},] coeff1=>op1, coeff2=>op2, ...; init_time=0.0)
TimeDependentSum(::Tuple, op::TimeDependentSum)
```

Lazy sum of operators with time-dependent coefficients. Wraps a [`LazySum`](@ref) `lazysum`, adding a `current_time` (or operator "clock") and a means of specifying time coefficients as functions of time (or numbers).

The coefficient type `Tf` may be specified explicitly. Time-dependent coefficients will be converted to this type on evaluation.
