```
expect(O::Union{AbstractQuantumObject,Vector{AbstractQuantumObject}}, ψ::Union{QuantumObject,Vector{QuantumObject}})
```

Expectation value of the [`Operator`](@ref) `O` with the state `ψ`. The state can be a [`Ket`](@ref), [`Bra`](@ref) or [`Operator`](@ref).

If `ψ` is a [`Ket`](@ref) or [`Bra`](@ref), the function calculates $\langle\psi|\hat{O}|\psi\rangle$.

If `ψ` is a density matrix ([`Operator`](@ref)), the function calculates $\textrm{Tr} \left[ \hat{O} \hat{\psi} \right]$

The function returns a real number if `O` is of `Hermitian` type or `Symmetric` type, and returns a complex number otherwise. You can make an operator `O` hermitian by using `Hermitian(O)`.

!!! note "List of observables and states"
    The observable `O` and state `ψ` can be given as a list of [`QuantumObject`](@ref), it returns a list of expectation values. If both of them are given as a list, it returns a `Matrix` of expectation values.


# Examples

```jldoctest
julia> ψ1 = 1 / √2 * (fock(10,2) + fock(10,4));

julia> ψ2 = coherent(10, 0.6 + 0.8im);

julia> a = destroy(10);

julia> expect(a' * a, ψ1) |> round
3.0 + 0.0im

julia> expect(Hermitian(a' * a), ψ1) |> round
3.0

julia> round.(expect([a' * a, a' + a, a], [ψ1, ψ2]), digits = 1)
3×2 Matrix{ComplexF64}:
 3.0+0.0im  1.0+0.0im
 0.0+0.0im  1.2-0.0im
 0.0+0.0im  0.6+0.8im
```
