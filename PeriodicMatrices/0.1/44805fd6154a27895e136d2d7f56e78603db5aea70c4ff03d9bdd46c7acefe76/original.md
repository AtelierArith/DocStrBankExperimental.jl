```
trace(A; rtol=sqrt(eps)) -> Atrace
```

Compute the trace of a continuous-time periodic matrix over one period.  For a continuous-time periodic matrix `A(t)`, the resulting `Atrace` is the mean value of the integral of the point-wise trace over a complete period.  The involved time integral are evaluated using the adaptive Gauss-Kronrod quadrature with a relative error tolerance `rtol`. 
