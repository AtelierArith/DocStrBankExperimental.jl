```
AbstractDVec{K,V}
```

Abstract data type for vector-like data structures with sparse storage. While conceptually `AbstractDVec`s represent elements of a vector space over a scalar type `V`, they are indexed by an arbitrary type `K` (could be non-integers) similar to dictionaries. They support the interface from [VectorInterface.jl](https://github.com/Jutho/VectorInterface.jl) and are designed to work well for quantum Monte Carlo with [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem) and for matrix-free linear algebra with [KrylovKit](https://github.com/Jutho/KrylovKit.jl).

Concrete implementations are available as [`PDVec`](@ref Main.DictVectors.PDVec), [`DVec`](@ref Main.DictVectors.DVec), and [`InitiatorDVec`](@ref Main.DictVectors.InitiatorDVec).

`AbstractDVec`s have a [`StochasticStyle`](@ref) which selects the spawning algorithm in `FCIQMC`. Looking up an element that is not stored in the `AbstractDVec` should return a zero, and setting a value to zero should remove it from the vector. To iterate over an `AbstractDVec`, use `keys`, `pairs`, or `values`. When possible, use reduction functions such as `sum` or `mapreduce`.

# Interface

The interface is similar to the `AbstractDict` interface, but with the changed behaviour as noted above.  Implement what would be needed for the `AbstractDict` interface (`pairs`, `keys`, `values`, `setindex!`, `getindex`, `delete!`, `length`, `empty`, `empty!`) and, in addition:

  * [`StochasticStyle`](@ref)
  * [`storage`](@ref) returns an `AbstractDict` storing the raw data with possibly different `valtype` than `V`.
  * [`deposit!`](@ref)

A default implementation for the [VectorInterface.jl](https://github.com/Jutho/VectorInterface.jl) interface is provided through the above functions.

See also [`DictVectors`](@ref Main.DictVectors), [`Interfaces`](@ref).
