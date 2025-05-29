# rescale

Rescale a vector to "un-standardize", the opposite of scale!().

```julia
rescale(x, xbar, xstd)

```

# Extended help

### Required arguments

```julia
* `x::Vector{Float64}`                 : Vector to be rescaled
* `xbar`                               : Mean value for rescaling
* `xstd`                               : Std for rescaling
```

### Return values

```julia
* `result::AbstractVector`             : Rescaled vector
```
