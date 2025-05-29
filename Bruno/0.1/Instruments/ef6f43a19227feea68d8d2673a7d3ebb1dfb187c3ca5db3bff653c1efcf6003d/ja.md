```
Stock(prices, name, timesteps_per_period, volatility)
Stock(price; kwargs...)
Stock(;kwargs)
```

金融商品のベース資産として使用するためのStock型を構築します。

## 引数

  * `prices`: 歴史的価格（1-D配列として入力）または現在の価格を数値 `<: Real` として入力します。
  * `name::String`: 株式の名前または株式ティッカーシンボル。デフォルトは ""。
  * `timesteps_per_period::Int64`: データのタイムステップのサイズ、特定の期間のタイムステップの数で、負の値にはできません。たとえば、関心のある期間が1年で、日次の株式データが使用される場合、`timesteps_per_period=252` です。デフォルトは `prices` 配列の長さまたは単一の価格（静的）株式の場合は0です。注意: `timesteps_per_period=0` の場合、Stockは「静的」要素を表し、`strategy_returns()` メソッドで使用することはできません。
  * `volatility`: 連続リターンの標準偏差で測定されるリターンのボラティリティ。

デフォルトでは、入力された `prices` 配列に対して `get_volatility()` を使用します。注意: `prices` に単一の数値が与えられた場合、ボラティリティを指定する必要があります。

## 例

```julia
Stock([1,2,3,4,5], "Example", 252, .05)

kwargs = Dict(
    :prices => [1, 2, 3, 4, 5], 
    :name => "Example", 
    :timesteps_per_period => 252, 
    :volatility => .05
);

Stock(;kwargs...)

Stock(40; volatility=.05)
```
