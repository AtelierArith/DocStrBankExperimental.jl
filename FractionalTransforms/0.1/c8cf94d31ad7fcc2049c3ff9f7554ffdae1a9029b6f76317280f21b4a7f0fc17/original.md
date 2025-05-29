```
frct(signal, α, p)
```

Computing the α order fractional cosine transform of the input **signal**.

# Example

```julia-repl
julia> frct([1,2,3], 0.5, 2)
3-element Vector{ComplexF64}:
1.707106781186547 + 0.9874368670764581im
1.5606601717798205 - 1.3964466094067267im
-0.3535533905932727 - 0.6982233047033652im
```

### References

```tex
@article{article,
author = {Pei, Soo-Chang and Yeh, Min-Hung},
year = {2001},
month = {07},
pages = {1198 - 1207},
title = {The discrete fractional cosine and sine transforms},
volume = {49},
journal = {Signal Processing, IEEE Transactions on},
doi = {10.1109/78.923302}
}
```
