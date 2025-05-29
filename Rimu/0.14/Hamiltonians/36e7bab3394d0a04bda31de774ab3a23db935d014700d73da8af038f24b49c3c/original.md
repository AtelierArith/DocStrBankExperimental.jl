```
ParitySymmetry(ham::AbstractHamiltonian{T}; even=true) <: AbstractHamiltonian{T}
```

Impose even or odd parity on all states and the Hamiltonian `ham` as controlled by the keyword argument `even`. Parity symmetry of the Hamiltonian is assumed. For some Hamiltonians, `ParitySymmetry` reduces the size of the Hilbert space by half.

`ParitySymmetry` performs a unitary transformation, leaving the eigenvalues unchanged and preserving the [`LOStructure`](@ref). This is achieved by changing the basis set to states with defined parity. Effectively, a non-even address $|α⟩$ is replaced by $\frac{1}{√2}(|α⟩ ± |ᾱ⟩)$ for even and odd parity, respectively, where `ᾱ == reverse(α)`.

# Notes

  * This modifier currently only works on [`starting_address`](@ref)s with an odd number of modes.
  * For odd parity, the [`starting_address`](@ref) of the underlying Hamiltonian cannot be symmetric.
  * If parity is not a symmetry of the Hamiltonian `ham` then the result is undefined.
  * `ParitySymmetry` works by modifying the [`offdiagonals`](@ref) iterator.

```jldoctest
julia> ham = HubbardReal1D(BoseFS(0,2,1))
HubbardReal1D(fs"|0 2 1⟩"; u=1.0, t=1.0)

julia> size(Matrix(ham))
(10, 10)

julia> size(Matrix(ParitySymmetry(ham)))
(6, 6)

julia> size(Matrix(ParitySymmetry(ham; odd=true)))
(4, 4)

julia> eigvals(Matrix(ham))[1] ≈ eigvals(Matrix(ParitySymmetry(ham)))[1]
true
```

See also [`TimeReversalSymmetry`](@ref).
