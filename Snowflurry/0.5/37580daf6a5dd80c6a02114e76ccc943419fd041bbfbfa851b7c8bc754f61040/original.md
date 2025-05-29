```
spin_up(T::Type{<:Complex}=ComplexF64)
```

Returns the `Ket` representation of the spin-up state.

The `Ket` stores values of type `T`, which is `ComplexF64` by default.

# Examples

```jldoctest
julia> ψ = spin_up()
2-element Ket{ComplexF64}:
1.0 + 0.0im
0.0 + 0.0im


```
