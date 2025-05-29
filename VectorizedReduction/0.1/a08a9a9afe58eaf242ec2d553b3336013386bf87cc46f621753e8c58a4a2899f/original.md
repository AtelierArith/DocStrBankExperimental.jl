```
vtmse(x::AbstractArray, y::AbstractArray; dims=:)
```

Compute the mean squared error between the vectors corresponding to the slices along the dimension `dims`. Threaded.

See also: [`vtrmse`](@ref)
