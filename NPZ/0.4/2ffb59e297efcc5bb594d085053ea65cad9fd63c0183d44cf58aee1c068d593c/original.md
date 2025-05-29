```
npzwrite(filename::AbstractString, x)
```

Write the variable `x` to the `npy` file `filename`.  Unlike `numpy`, the extension `.npy` is not appened to `filename`.

!!! warn "Warning"
    Any existing file with the same name will be overwritten.


# Examples

```julia
julia> npzwrite("abc.npy", zeros(3))

julia> npzread("abc.npy")
3-element Array{Float64,1}:
 0.0
 0.0
 0.0
```
