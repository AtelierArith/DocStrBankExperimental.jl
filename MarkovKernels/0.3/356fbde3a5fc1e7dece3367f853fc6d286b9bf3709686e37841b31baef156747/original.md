```
compose(L2::AbstractLikelihood, L1::AbstractLiklelihood)
```

Computes L3, the composition of L2 ∘ L1 i.e.,

L3(x) = L1(x) * L2(x)

See also [`∘`](@ref)
