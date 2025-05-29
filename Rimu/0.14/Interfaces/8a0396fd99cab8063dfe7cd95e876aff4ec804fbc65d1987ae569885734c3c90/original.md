```
AbstractHamiltonian{T} <: AbstractOperator{T}
```

Supertype that provides an interface for linear operators over a linear space with scalar type `T` that are suitable for FCIQMC (with [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem)). Indexing is done with addresses (typically not integers) from an address space that may be large (and will not need to be completely generated).

`AbstractHamiltonian` instances operate on vectors of type [`AbstractDVec`](@ref) from the module `DictVectors` and work well with addresses of type [`AbstractFockAddress`](@ref Main.BitStringAddresses.AbstractFockAddress) from the module `BitStringAddresses`. The type works well with the external package [KrylovKit.jl](https://github.com/Jutho/KrylovKit.jl).

For available implementations see [`Hamiltonians`](@ref Main.Hamiltonians).

# Interface

Basic interface methods to implement:

  * [`starting_address(::AbstractHamiltonian)`](@ref)
  * [`diagonal_element(::AbstractHamiltonian, address)`](@ref)
  * [`num_offdiagonals(::AbstractHamiltonian, address)`](@ref)
  * [`get_offdiagonal(::AbstractHamiltonian, address, chosen::Integer)`](@ref) (optional, see   below)

Optional additional methods to implement:

  * [`LOStructure(::Type{typeof(lo)})`](@ref LOStructure): defaults to `AdjointUnknown`
  * [`dimension(::AbstractHamiltonian, addr)`](@ref Main.Hamiltonians.dimension): defaults to dimension of address space
  * [`allows_address_type(h::AbstractHamiltonian, type)`](@ref): defaults to `type :< typeof(starting_address(h))`
  * [`momentum(::AbstractHamiltonian)`](@ref Main.Hamiltonians.momentum): no default

Provides the following functions and methods:

  * [`offdiagonals`](@ref): iterator over reachable off-diagonal matrix elements
  * [`random_offdiagonal`](@ref): function to generate random off-diagonal matrix element
  * `*(H, v)`: deterministic matrix-vector multiply (allocating)
  * `H(v)`: equivalent to `H * v`.
  * `mul!(w, H, v)`: mutating matrix-vector multiply.
  * [`dot(x, H, v)`](@ref Main.Hamiltonians.dot): compute `x⋅(H*v)` minimizing allocations.
  * `H[address1, address2]`: indexing with `getindex()` - mostly for testing purposes (slow!)
  * [`BasisSetRepresentation`](@ref Main.ExactDiagonalization.BasisSetRepresentation): construct a basis set repesentation
  * [`sparse`](@ref Main.ExactDiagonalization.sparse), [`Matrix`](@ref): construct a (sparse) matrix representation

Alternatively to the above, [`offdiagonals`](@ref) can be implemented instead of [`get_offdiagonal`](@ref). Sometimes this can be done efficiently. In this case [`num_offdiagonals`](@ref) should provide an upper bound on the number of elements obtained when iterating [`offdiagonals`](@ref).

See also [`Hamiltonians`](@ref Main.Hamiltonians), [`Interfaces`](@ref), [`AbstractOperator`](@ref), [`AbstractObservable`](@ref).
