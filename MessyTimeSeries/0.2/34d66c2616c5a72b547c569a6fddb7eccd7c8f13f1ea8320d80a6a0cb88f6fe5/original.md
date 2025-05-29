```
solve_discrete_lyapunov(A::AbstractArray{Float64,2}, Q::SymMatrix)
```

Use a bilinear transformation to convert the discrete Lyapunov equation to a continuous Lyapunov equation, which is then solved using BLAS.

The notation used for representing the discrete Lyapunov equation is

$P - APA' = Q$,

where $P$ and $Q$ are symmetric. This equation is transformed into

$B'P + PB = -C$

# References

Kailath (1980, page 180)
