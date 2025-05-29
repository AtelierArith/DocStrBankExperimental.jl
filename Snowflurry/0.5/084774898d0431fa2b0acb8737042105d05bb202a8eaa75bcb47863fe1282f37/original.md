```
normalize!(x::Ket)
```

Normalizes Ket `x` such that its magnitude becomes unity.

```jldoctest
julia> ψ = Ket([1., 2., 4.])
3-element Ket{ComplexF64}:
1.0 + 0.0im
2.0 + 0.0im
4.0 + 0.0im

julia> normalize!(ψ)
3-element Ket{ComplexF64}:
0.2182178902359924 + 0.0im
0.4364357804719848 + 0.0im
0.8728715609439696 + 0.0im
```
