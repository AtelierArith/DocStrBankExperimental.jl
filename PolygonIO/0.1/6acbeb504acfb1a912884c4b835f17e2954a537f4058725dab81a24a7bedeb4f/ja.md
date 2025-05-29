```
last_trade_crypto_pair(opts::PolyOpts, from="BTC", to="USD")
```

暗号通貨ペアの最後の取引ティックを取得します。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * from: ペアの「from」シンボル。
  * to: ペアの「to」シンボル。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> last_trade_crypto_pair(opts, "BTC", "USD")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v1*last_crypto**from___to**anchor を参照してください。
