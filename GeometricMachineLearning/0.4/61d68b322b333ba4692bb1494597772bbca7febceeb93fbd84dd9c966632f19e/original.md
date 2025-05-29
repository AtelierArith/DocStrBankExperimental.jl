```
DataLoader(solution)
```

Make an instance of `DataLoader` for a `GeometricSolution`.

`GeometricSolution`s are imported from the the package [`GeometricSolutions.jl`](https://github.com/JuliaGNI/GeometricSolutions.jl).

# Arguments

This functor for [`DataLoader`](@ref) also has the keyword arguments 

  * `autoencoder = false` and
  * `suppress_info = false`.

See the docstring for [`DataLoader(::AbstractArray{<:Number, 3})`](@ref).

# Implementation

Internally this stores the data as a tensor where the third axis has length 1.
