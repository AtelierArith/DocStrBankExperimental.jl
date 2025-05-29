```
CCSRetroFit <: Network
```

このノードは、[`RefNetworkNodeRetrofit`](@ref)ノードへのCO₂捕集レトロフィットへの投資を可能にします。捕集プロセスは、変数`:cap_use`を通じて実装されています。

`co2_proxy`は`input`リソースとして指定する必要はありません。

# フィールド

  * **`id`**はノードの名前/識別子です。
  * **`cap::TimeProfile`**は設置された容量です。
  * **`opex_var::TimeProfile`**は捕集されたCO₂単位あたりの変動運用コストです。
  * **`opex_fixed::TimeProfile`**は固定運用コストです。
  * **`input::Dict{<:Resource, <:Real}`**は変換値`Real`を持つ入力`Resource`です。
  * **`output::Dict{<:Resource, <:Real}`**は変換値`Real`を持つ生成された`Resource`です。CO₂インスタンスは、CO₂捕集が適切に適用されるために含まれる必要があります。
  * **`co2_proxy::Resource`**は、`RefNetworkNodeRetrofit`から`CCSRetroFit`ノードへのCO₂フローを内部的に計算するために使用される`Resource`のインスタンスです。
  * **`data::Array{<:Data}`**は追加データ（例：投資用）です。
