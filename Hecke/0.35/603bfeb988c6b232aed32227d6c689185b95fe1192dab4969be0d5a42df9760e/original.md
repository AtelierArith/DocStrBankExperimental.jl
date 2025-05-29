```
normred(a::AlgAssRelOrdIdl{S, T}, O::AlgAssRelOrd{S, T}; copy::Bool = true)
  where { S, T, U } -> T
```

Returns the reduced norm of $a$ considered as an (possibly fractional) ideal of $O$. It is assumed that the algebra containing $a$ is simple and central.
