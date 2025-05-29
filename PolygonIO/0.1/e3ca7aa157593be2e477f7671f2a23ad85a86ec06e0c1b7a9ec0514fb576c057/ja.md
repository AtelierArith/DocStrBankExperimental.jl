```
crypto_daily_open_close(opts::PolyOpts, from="BTC", to="USD", date="2020-10-14"; adjusted=true)
```

特定の日に暗号通貨シンボルの始値と終値を取得します。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * from: ペアの「from」シンボル。
  * to: ペアの「to」シンボル。
  * date: YYYY-MM-DD形式での要求された始値/終値の日付。
  * adjusted: 結果がスプリットに対して調整されているかどうか。デフォルトでは、結果は調整されています。これをfalseに設定すると、スプリットに対して調整されていない結果が得られます。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> crypto_daily_open_close(opts, "BTC", "USD", "2020-10-14")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v1*open-close_crypto**from___to___date**anchorを参照してください。
