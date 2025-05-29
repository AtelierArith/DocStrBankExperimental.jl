```
apply_instruction!(state::Ket, gate::Gate)
```

Update the `state` by applying a `gate` to it.

# Examples

```jldoctest
julia> ψ_0 = fock(0, 2)
2-element Ket{ComplexF64}:
1.0 + 0.0im
0.0 + 0.0im


julia> apply_instruction!(ψ_0, sigma_x(1))
2-element Ket{ComplexF64}:
0.0 + 0.0im
1.0 + 0.0im

```
