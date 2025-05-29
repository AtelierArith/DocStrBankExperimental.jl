```
historic_forex_ticks(opts::PolyOpts, from="AUD", to="USD", date="2020-10-14"; limit=100, kwargs...)
```

外国為替通貨ペアの履歴ティックを取得します。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * from: 通貨ペアの「from」シンボル。例: USD/JPYの場合、fromはUSDになります。
  * to: 通貨ペアの「to」シンボル。例: USD/JPYの場合、toはJPYになります。
  * date: 取得する履歴ティックの日付。
  * limit: レスポンスのサイズを制限します。最大10000。デフォルトは100。
  * kwargs: Poly APIに渡す追加のパラメータ。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> historic_forex_ticks(opts, "AUD", "AUD", "2020-10-14")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * レスポンス属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v1*historic_forex**from___to___date**anchorを参照してください。
