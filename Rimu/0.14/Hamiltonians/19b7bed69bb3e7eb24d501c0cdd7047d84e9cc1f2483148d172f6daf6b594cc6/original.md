```
TimeReversalSymmetry(ham::AbstractHamiltonian{T}; even=true) <: AbstractHamiltonian{T}
```

Impose even or odd time reversal on all states and the Hamiltonian `ham` as controlled by the keyword argument `even`. If time reversal is a symmetry of the Hamiltonian it will block (reducing Hilbert space dimension) preserving the eigenvalues and [`LOStructure`](@ref).

# Notes

  * This modifier only works two component [`starting_address`](@ref)es.
  * For odd time reversal symmetry, the [`starting_address`](@ref) of the underlying Hamiltonian must not be symmetric.
  * If time reversal is not a symmetry of the Hamiltonian `ham` then the result is undefined.
  * `TimeReversalSymmetry` works by modifying the [`offdiagonals`](@ref) iterator.

```jldoctest
julia> ham = HubbardMom1D(FermiFS2C((1,0,1),(0,1,1)));

julia> size(Matrix(ham))
(3, 3)

julia> size(Matrix(TimeReversalSymmetry(ham)))
(2, 2)

julia> size(Matrix(TimeReversalSymmetry(ham, even=false)))
(1, 1)

julia> eigvals(Matrix(TimeReversalSymmetry(ham)))[1] ≈ eigvals(Matrix(ham))[1]
true
```

See also [`ParitySymmetry`](@ref).
