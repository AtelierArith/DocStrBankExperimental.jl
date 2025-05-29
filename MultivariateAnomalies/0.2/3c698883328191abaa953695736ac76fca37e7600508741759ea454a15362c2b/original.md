```
init_KDE(K::Array{Float64, 2})
init_KDE(T::Int)
```

Returns `KDE_out` object for usage in `KDE!()`. Use either a Kernel matrix `K` or the number of time steps/observations `T` as argument.
