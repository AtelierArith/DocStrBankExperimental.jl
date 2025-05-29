```
norm(A::QuantumObject, p::Real)
```

Return the standard vector `p`-norm or [Schatten](https://en.wikipedia.org/wiki/Schatten_norm) `p`-norm of a [`QuantumObject`](@ref) depending on the type of `A`:

  * If `A` is either [`Ket`](@ref), [`Bra`](@ref), [`OperatorKet`](@ref), or [`OperatorBra`](@ref), returns the standard vector `p`-norm (default `p=2`) of `A`.
  * If `A` is either [`Operator`](@ref) or [`SuperOperator`](@ref), returns [Schatten](https://en.wikipedia.org/wiki/Schatten_norm) `p`-norm (default `p=1`) of `A`.

# Examples

```jldoctest
julia> ψ = fock(10, 2)

Quantum Object:   type=Ket()   dims=[10]   size=(10,)
10-element Vector{ComplexF64}:
 0.0 + 0.0im
 0.0 + 0.0im
 1.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im

julia> norm(ψ)
1.0
```
