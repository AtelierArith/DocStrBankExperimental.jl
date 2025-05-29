```
real_time_currency_conversion(opts::PolyOpts, from="AUD", to="USD"; amount=100, precision=2)
```

最新の市場換算レートを使用して通貨換算を取得します。両方向に換算できることに注意してください。たとえば、USDからCAD、またはCADからUSDです。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * from: ペアの「from」シンボル。
  * to: ペアの「to」シンボル。
  * amount: 換算する金額。
  * precision: 換算の小数精度。デフォルトは2で、小数点以下2桁の精度です。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> real_time_currency_conversion(opts, "AUD", "USD"; amount=100, precision=2)
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v1*conversion**from___to**anchorを参照してください。
