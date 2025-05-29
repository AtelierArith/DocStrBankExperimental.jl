```
tidyup(A::QuantumObject, tol::Real=settings.tidyup_tol)
```

Given a [`QuantumObject`](@ref) `A`, check the real and imaginary parts of each element separately. Remove the real or imaginary value if its absolute value is less than `tol`.
