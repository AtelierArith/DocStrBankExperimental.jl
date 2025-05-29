```
intt(y::Array{T,1}, g, q) -> Array{T,1}
```

Inverse Number Theoretic Transform implementation directly from the formula.

$x_k = N^{-1} \sum_{n=1}^N{\bar{x}_n g^{-(n-1)(k-1)} } \mod q$

The same input parameters constraints as for `ntt` function must be applied
