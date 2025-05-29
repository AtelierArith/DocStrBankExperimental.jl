```
 tvmeval(A, t) -> Aval::Vector{Matrix}
```

Evaluate the time response of a periodic matrix.

For the periodic matrix `A(t)` and the vector of time values `t`,  the vector `Aval` of time values is computed such that  `Aval[i] = A(t[i])` for each time value `t[i]`. 
