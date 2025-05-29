```
 pslyapdkr(A, C; adj = true) -> X
```

Solve the periodic discrete-time Lyapunov matrix equation

```
  A'σXA + C = X, if adj = true,
```

or 

```
  A*X*A' + C =  σX, if adj = false,
```

where `σ` is the forward shift operator `σX(i) = X(i+1)`.   The periodic matrix `A` must not have characteristic multipliers on the unit circle.                The periodic matrices `A` and `C` are either stored as 3-dimensional arrays or as as vectors of matrices. 

The Kronecker product expansion of equations is employed and therefore  this function is not recommended for large order matrices or large periods.
