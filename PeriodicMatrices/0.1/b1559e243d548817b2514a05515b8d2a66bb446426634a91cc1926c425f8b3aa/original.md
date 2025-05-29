```
isconstant(A)
isconstant(A::PeriodicFunctionMatrix; check_const = false, atol = 1000*eps(), rtol = sqrt(eps()) )
```

Constancy check of a periodic matrix. For a periodic function matrix `A(t)`,  an optional optimization-based constancy check can be performed using `check_const = true`, with the absolute and relative tolerances `atol` and `rtol`, respectively.   
