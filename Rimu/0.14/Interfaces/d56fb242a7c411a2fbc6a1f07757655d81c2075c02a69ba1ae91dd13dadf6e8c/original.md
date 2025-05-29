```
AbstractOperator{T} <: AbstractObservable{T}
```

Supertype that provides an interface for linear operators over a linear space with elements of type `T` (returned by [`eltype`](@ref)) and general (custom type) indices called 'addresses'.

`AbstractOperator` instances operate on vectors of type [`AbstractDVec`](@ref) from the module `DictVectors` and work well with addresses of type [`AbstractFockAddress`](@ref Main.BitStringAddresses.AbstractFockAddress) from the module `BitStringAddresses`.

The defining feature of an `AbstractOperator` is that it can be applied to a vector with [`mul!(y, op, x)`](@ref LinearAlgebra.mul!) and that three-way dot products can be calculated with [`dot(x, op, y)`](@ref LinearAlgebra.dot).

The `AbstractOperator` type is useful for defining operators that are not necessarily Hamiltonians, but that can be used in the context of a [`ProjectorMonteCarloProblem`](@ref) as observable operators in a [`ReplicaStrategy`](@ref Rimu.ReplicaStrategy), e.g. for defining correlation functions. In contrast to [`AbstractHamiltonian`](@ref)s, `AbstractOperator`s do not need to have a [`starting_address`](@ref). Moreover, the `eltype` of an `AbstractOperator` can be a vector value whereas [`AbstractHamiltonian`](@ref)s requre a scalar `eltype`.

```
AbstractHamiltonian{T} <: AbstractOperator{T} <: AbstractObservable{T}
```

The `AbstractOperator` type is part of the [`AbstractObservable`](@ref) hierarchy. It is more restrictive than `AbstractObservable` in that it requires the interface for the generation of diagonal and off-diagonal elements.

For concrete implementations see [`Hamiltonians`](@ref Main.Hamiltonians). In order to implement a Hamiltonian for use in [`ProjectorMonteCarloProblem`](@ref) or [`ExactDiagonalizationProblem`](@ref) use the type [`AbstractHamiltonian`](@ref) instead.

# Interface

Basic interface methods to implement:

  * [`allows_address_type(op, type)`](@ref)
  * [`diagonal_element(op, address)`](@ref)
  * [`num_offdiagonals(op, address)`](@ref) and
  * [`get_offdiagonal(op, address, chosen)`](@ref) or [`offdiagonals`](@ref)

Optional additional methods to implement:

  * [`VectorInterface.scalartype(op)`](@ref): defaults to `eltype(eltype(op))`
  * [`LOStructure(::Type{typeof(op)})`](@ref LOStructure): defaults to `AdjointUnknown`
  * [`dimension(op, addr)`](@ref Main.Hamiltonians.dimension): defaults to dimension of address space

In order to calculate observables efficiently, it may make sense to implement custom methods for [`Interfaces.dot_from_right(x, op, y)`](@ref) and [`LinearAlgebra.mul!(y, op, x)`](@ref).

See also [`AbstractHamiltonian`](@ref), [`Interfaces`](@ref).
