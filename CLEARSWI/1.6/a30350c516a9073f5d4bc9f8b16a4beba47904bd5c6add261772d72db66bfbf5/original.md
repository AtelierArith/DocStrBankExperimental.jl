```
createIntensityProjection(S::AbstractArray{T,3}, func, d=7) where T
```

Calculates an intensity projection over the 3rd dimension of `S` with the function `func` over `d` slices. Good function are `minimum`, `maximum`, `mean`, `std`, ...

# Examples

```julia-repl
julia> using Statistics
julia> a = rand(Float64, (64,64,20))
julia> createIntensityProjection(a, std)
```
