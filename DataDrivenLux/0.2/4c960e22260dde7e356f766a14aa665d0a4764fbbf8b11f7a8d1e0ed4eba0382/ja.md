```julia
struct LayeredDAG{__T_layers} <: LuxCore.AbstractLuxWrapperLayer{:layers}
```

異なる [`DecisionLayer`](@ref)s から構成される層状の有向非巡回グラフのコンテナです。

# フィールド

  * `layers`
