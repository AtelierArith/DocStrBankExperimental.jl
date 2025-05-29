```
historic_crypto_trades(opts::PolyOpts, from="BTC", to="USD", date="2020-10-14"; limit=100, kwargs...)
```

暗号通貨ペアの過去の取引ティックを取得します。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * from: 暗号ペアの「from」シンボル。
  * to: 暗号ペアの「to」シンボル。
  * date: 取得する過去のティックの日付。
  * limit: レスポンスのサイズを制限します。最大10000。デフォルトは100。
  * kwargs: リクエストに渡す追加の引数。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> historic_crypto_trades(opts, "BTC", "USD", "2020-10-14")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * レスポンス属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v1*historic_crypto**from___to___date**anchorを参照してください。
