```
RefNetworkNodeRetrofit <: NetworkNodeWithRetrofit
```

このノードは、`NetworkNode`にCO₂捕集を改造することを可能にします。

これは、CO₂が排出されない[`RefNetworkNode`](@extref EnergyModelsBase.RefNetworkNode)ノードに対応しています。代わりに、CO₂は`co2_proxy`に転送され、その後、捕集されるか排出されるノード（[`CCSRetroFit`](@ref)）に供給されます。

`co2_proxy`は`output`リソースとして指定する必要はありません。

# フィールド

  * **`id`**はノードの名前/識別子です。
  * **`cap::TimeProfile`**は設置された容量です。
  * **`opex_var::TimeProfile`**は生産されたエネルギー単位あたりの変動運用コストです。
  * **`opex_fixed::TimeProfile`**は固定運用コストです。
  * **`input::Dict{<:Resource, <:Real}`**は変換値`Real`を持つ入力`Resource`です。
  * **`output::Dict{<:Resource, <:Real}`**は変換値`Real`を持つ生成された`Resource`です。CO₂捕集が適切に適用されるためには`co2_proxy`を含める必要があります。
  * **`co2_proxy::Resource`**は、`RefNetworkNodeRetrofit`から`CCSRetroFit`ノードへのCO₂フローを内部的に計算するために使用される`Resource`のインスタンスです。
  * **`data::Array{<:Data}`**は追加データ（例：投資用）です。
