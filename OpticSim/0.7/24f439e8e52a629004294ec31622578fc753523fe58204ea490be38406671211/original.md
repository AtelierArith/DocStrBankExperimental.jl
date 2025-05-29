```
AcceleratedParametricSurface{T,N,S} <: ParametricSurface{T,N}
```

Wrapper class for [`ParametricSurface`](@ref)s where analytical intersection isn't feasible (e.g. [`ZernikeSurface`](@ref), [`ChebyshevSurface`](@ref)). The surface is instead triangulated and an iterative (newton raphson) process carried out to determine precise ray intersection points. `S` is the type of the ParametricSurface being wrapped.

```julia
AcceleratedParametricSurface(surf::ParametricSurface{T,N}, numsamples::Int = 17; interface::NullOrFresnel{T} = nullinterface(T))
```
