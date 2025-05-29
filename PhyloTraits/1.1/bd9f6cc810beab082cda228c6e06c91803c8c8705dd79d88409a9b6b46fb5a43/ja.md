```
rand!(rng::AbstractRNG,
      end::AbstractVector{Int},
      model::TraitSubstitutionModel,
      t::Float64,
      start::AbstractVector{Int})
```

長さ `t` の1つのエッジに沿って離散的な特性をシミュレートします。 [`rand`](@ref PhyloTraits.rand) のように、シミュレートされた値を格納するために `end` をその場で修正します。
