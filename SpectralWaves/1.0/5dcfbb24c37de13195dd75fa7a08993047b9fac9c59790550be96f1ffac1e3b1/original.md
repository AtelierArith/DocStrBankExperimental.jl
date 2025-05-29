```
convolution_range(m::Integral, M::Integral, n::Integer)
```

Compute range `r` of indices of a central part of convolution vector corresponding to the `m`-th order of convolution, where `M` is the maximum order of convolution, `N` is the length of convolution vector corresponding to the `M`-th order of convolution, and `ℐ` is the number of harmonics.

# Examples

```julia-repl
julia> m = 1; M = 3; ℐ = 5; c_range = convolution_range(m, M, ℐ)
11:31
```
