```
AbstractIteratedLimits{d,T}
```

Supertype for limits of integration over a domain with elements of type `SVector{d,T}`. In order to work with iterated integration, the following methods must be implemented

# Interface

  * [`segments`](@ref): returns an iterator over intervals to integrate in the current dimension
  * [`fixandeliminate`](@ref): return another limit object with one of the variables of integration eliminated

the domain of integration must be convex.
