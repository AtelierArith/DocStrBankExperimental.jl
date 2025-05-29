A structure representing a Bra (i.e., a row vector of complex values). A Bra is created as the complex conjugate of a Ket.

# Examples

```jldoctest
julia> ψ = fock(1, 3)
3-element Ket{ComplexF64}:
0.0 + 0.0im
1.0 + 0.0im
0.0 + 0.0im


julia> _ψ = Bra(ψ)
3-element Bra{ComplexF64}:
0.0 - 0.0im
1.0 - 0.0im
0.0 - 0.0im


julia> _ψ * ψ    # A Bra times a Ket is a scalar
1.0 + 0.0im

julia> ψ*_ψ     # A Ket times a Bra is an operator
(3, 3)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im


```
