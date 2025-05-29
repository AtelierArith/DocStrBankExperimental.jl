```
hvector(K)
hvector(fv)
```

Compute the h-vector of complex `K` by calling `fvector(K)`, or compute the h-vector corresponding to vector `fv`.

See [`fvector`](@ref) for details on the f-vector of a simplicial complex. The f-polynomial is the polynomial $F(x)$ with coefficient $f_i$ in degree $d+1-i$; the h-vector is the coefficients of $F(x-1)$ in decreasing order of degree.
