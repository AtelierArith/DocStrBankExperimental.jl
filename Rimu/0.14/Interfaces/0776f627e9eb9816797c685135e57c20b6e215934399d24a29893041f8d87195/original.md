```
AbstractObservable{T}
```

Most permissive supertype for operators in the type hierarchy:

```
AbstractHamiltonian{T} <: AbstractOperator{T} <: AbstractObservable{T}
```

`AbstractObservable` provides an interface for operators that can appear in a three-way dot product [`dot(x, op, y)`](@ref LinearAlgebra.dot) with two vectors of type [`AbstractDVec`](@ref). The result is a value of type `T`, which is also returned by the [`eltype`](@ref) function. This may be a vector type associated with a scalar type returned by the [`scalartype`](@ref) function.

The `AbstractObservable` type is useful for defining observables that can be calculated in the context of a [`ProjectorMonteCarloProblem`](@ref) using [`AllOverlaps`](@ref Main.Hamiltonians).

# Interface

Basic interface methods to implement:

  * [`Interfaces.dot_from_right(x, op, y)`](@ref)
  * [`allows_address_type(op, type)`](@ref)

Optional additional methods to implement:

  * [`VectorInterface.scalartype(op)`](@ref): defaults to `eltype(eltype(op))`
  * [`LOStructure(::Type{typeof(op)})`](@ref LOStructure): defaults to `AdjointUnknown`

See also [`AbstractOperator`](@ref), [`AbstractHamiltonian`](@ref), [`Interfaces`](@ref).
