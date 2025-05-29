```
DGMultiBasis(element_type, polydeg; approximation_type = Polynomial(), kwargs...)
```

DGMultiソルバーのための基底を構築します。 "StartUpDG.RefElemData"オブジェクトを返します。 `kwargs`引数は、`RefElemData`の追加のキーワード引数であり、`quad_rule_vol`などがあります。これらは[`DGMulti`](@ref)で使用される`RefElemData_kwargs`と同じです。詳細については、[StartUpDG.jlのドキュメント](https://jlchan.github.io/StartUpDG.jl/dev/)を参照してください。
