```
fock(i, hspace_size,T::Type{<:Complex}=ComplexF64)
```

Returns the `i`th Fock basis of a Hilbert space with size `hspace_size` as a Ket.

!!! note
    Fock basis states numbering starts at 0.


The Ket contains values of type `T`, which by default is ComplexF64.

# Examples

```jldoctest
julia> ψ = fock(0, 3)
3-element Ket{ComplexF64}:
1.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im


julia> ψ = fock(1, 3)
3-element Ket{ComplexF64}:
0.0 + 0.0im
1.0 + 0.0im
0.0 + 0.0im


julia> ψ = fock(1, 3, ComplexF32) # specifying a type other than ComplexF64
3-element Ket{ComplexF32}:
0.0f0 + 0.0f0im
1.0f0 + 0.0f0im
0.0f0 + 0.0f0im
```
