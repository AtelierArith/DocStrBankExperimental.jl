```
EuroCallOption(;kwargs...)
EuroCallOption(widget, strike_price, maturity, risk_free_rate, values_library)
```

`Widget`型の基礎資産を持つEuroCallOptionを構築します。

## 引数

  * `widget`: 基礎資産
  * `strike_price`: 満期時に基礎資産を購入するための契約価格
  * `maturity`: オプションの満期までの時間（暗黙の時間期間に関して）。デフォルトは1。
  * `risk_free_rate`: 市場のリスクフリー金利。デフォルトは.02。
  * `values_library`: 価格設定関数から返される値の辞書。デフォルトでは空の辞書が初期化されます。理論的なオプション価格を読み込むには`price!()`関数を使用します。

## 例

```julia
stock = Stock([1,2,4,3,5,3]);

EuroCallOption(stock, 10)

kwargs = Dict(:widget=>stock, :strike_price=>10, :maturity=>1, :risk_free_rate=>.02);
EuroCallOption(;kwargs...)
```
