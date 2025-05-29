```
EuroPutOption(widget, strike_price; kwargs...)
EuroPutOption(;kwargs...)
```

`Widget`型の基礎資産を持つEuroPutOptionを構築します。

## 引数

  * `widget`: 基礎資産。
  * `strike_price`: 満期時に基礎資産を購入するための契約価格。
  * `maturity`: オプションの満期までの時間（暗黙の時間期間に対して）。デフォルトは1。
  * `risk_free_rate`: 市場のリスクフリー金利。デフォルトは.02。
  * `values_library`: プライシングモデルから返される値。デフォルトでは空の辞書で初期化されます。理論的なオプション価格を読み込むには`price!()`関数を使用します。

## 例

```julia
stock = Stock([1,2,4,3,5,3]);

EuroPutOption(stock, 10)

kwargs= Dict(:widget=>stock, :strike_price=>10, :maturity=>1, :risk_free_rate=>.02);
EuroPutOption(;kwargs...)
```
