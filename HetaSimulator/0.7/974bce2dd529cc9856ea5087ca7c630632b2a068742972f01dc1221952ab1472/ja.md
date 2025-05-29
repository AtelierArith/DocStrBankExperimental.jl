```
add_measurements!(
  scenario::Scenario,
  df::DataFrame;
  kwargs...
)
```

`Scenario`に測定値を追加します

引数:

  * `scenario` : [`Scenario`](@ref)型のシミュレーションシナリオ
  * `df` : 通常は[`read_measurements`](@ref)関数で取得される測定値を含む`DataFrame`
  * `subset` : `Scenario`に追加される測定値のサブセット。デフォルトの`Pair{Symbol, Symbol}[]`は`df`からすべての測定値を追加します
