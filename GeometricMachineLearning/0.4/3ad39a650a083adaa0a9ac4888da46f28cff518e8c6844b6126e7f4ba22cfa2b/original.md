```
DataLoader(ensemble_solution)
```

Make an instance of `DataLoader` for a `EnsembleSolution`.

`EnsembleSolution`s are imported from the the package [`GeometricSolutions.jl`](https://github.com/JuliaGNI/GeometricSolutions.jl).

# Arguments

This functor for `DataLoader` also has the keyword arguments 

  * `autoencoder = false` and
  * `suppress_info = false`.

See the docstring for [`DataLoader(::AbstractArray{<:Number, 3})`](@ref).

# Implementation

Internally this stores the data as a tensor where the third axis has length equal to the number of solutions in the ensemble.
