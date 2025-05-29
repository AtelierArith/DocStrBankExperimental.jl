```
add_scenarios!(
  platform::Platform,
  df::DataFrame;
  subset::AbstractVector{P} = Pair{Symbol, Symbol}[]
) where P <: Pair{Symbol, Symbol}
```

`Platform`に新しい`Scenario`を追加します。

引数:

  * `platform` : [`Platform`](@ref)型のプラットフォーム
  * `df` : 通常は[`read_scenarios`](@ref)関数で取得されるシナリオ設定を持つ`DataFrame`
  * `subset` : `platform`に追加されるシナリオのサブセット。デフォルトの`Pair{Symbol, Symbol}[]`は`df`からすべてのシナリオを追加します。
