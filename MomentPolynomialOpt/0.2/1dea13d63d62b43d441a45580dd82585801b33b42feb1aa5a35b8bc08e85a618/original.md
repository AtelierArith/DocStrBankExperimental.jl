```
get_minimizers(M, , t::Int64 = 2*M[:degree]-1)
```

Return the minimizer points  of the optimized moment program `M`, using moments of degree <=t (default: twice the order of the relaxation minus 2)

```julia
get_minimizer(M)

[1.41421 1.73205; 1.41421 1.41421; 1.41421 -1.73205]
```
