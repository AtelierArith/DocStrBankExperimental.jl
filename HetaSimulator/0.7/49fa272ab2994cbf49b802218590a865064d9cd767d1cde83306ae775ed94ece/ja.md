```
add_measurements!(
  platform::Platform,
  df::DataFrame;
  kwargs...
)
```

`Scenario`に測定値を追加します。

引数:

  * `platform` : [`Platform`](@ref) 型のプラットフォーム
  * `df` : 通常は[`read_measurements`](@ref)関数で取得される測定値を含む`DataFrame`
  * `subset` : `Scenario`に追加される測定値のサブセット。デフォルトの`Pair{Symbol, Symbol}[]`は`df`からすべての測定値を追加します。
