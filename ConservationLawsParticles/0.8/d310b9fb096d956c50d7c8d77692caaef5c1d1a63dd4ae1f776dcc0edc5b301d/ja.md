```julia
interaction(
    mod::ConservationLawsParticles.AbstractModel,
    i::Integer,
    j::Integer
) -> Any

```

種 `i` に対して種 `j` が及ぼす相互作用を返します。
