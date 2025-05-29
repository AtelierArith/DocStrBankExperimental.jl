```
set!(solution, kwargs...)
```

Set the fields of a solution. For example, use

T0 = rand(4) S0(z) = exp(-z^2/10) set!(solution, T=T0, S=S0)

To set solution.T and solution.S to T0 and S0.
