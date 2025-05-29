```
DiffEqArrayOperator(A[; update_func])
```

Represents a time-dependent linear operator given by an AbstractMatrix. The update function is called by `update_coefficients!` and is assumed to have the following signature:

```
update_func(A::AbstractMatrix,u,p,t) -> [modifies A]
```
