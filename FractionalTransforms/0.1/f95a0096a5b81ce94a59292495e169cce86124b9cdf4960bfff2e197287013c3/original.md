```
frst(signal, α, p)
```

Computing the α order fractional sine transform of the input **signal**.

# Example

```julia-repl
julia> frst([1,2,3], 0.5, 2)
3-element Vector{ComplexF64}:
1.707106781186548 + 1.207106781186547im
1.9999999999999998 - 1.7071067811865481im
-1.1213203435596437 - 1.2071067811865468im
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
