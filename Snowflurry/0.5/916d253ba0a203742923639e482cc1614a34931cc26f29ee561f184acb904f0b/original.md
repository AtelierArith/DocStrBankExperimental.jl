```
spin_down(T::Type{<:Complex}=ComplexF64)
```

Returns the `Ket` representation of the spin-down state.

The `Ket` stores values of type `T`, which is `ComplexF64` by default.

# Examples

```jldoctest
julia> ψ = spin_down()
2-element Ket{ComplexF64}:
0.0 + 0.0im
1.0 + 0.0im


```
