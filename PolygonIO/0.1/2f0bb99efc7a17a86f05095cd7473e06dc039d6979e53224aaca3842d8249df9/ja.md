```
crypto_snapshot_ticker_full_book(opts::PolyOpts, ticker="X:BTCUSD")
```

単一のティッカーの現在のレベル2ブックを取得します。これはすべての取引所からの結合されたブックです。注意: スナップショットデータは東部標準時の午前12時にクリアされ、取引所からデータが受信されるとポピュレートされます。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * ticker: 暗号通貨ティッカー。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> crypto_snapshot_ticker_full_book(opts, "X:BTCUSD")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*snapshot*locale*global*markets*crypto*tickers**ticker**book*anchor を参照してください。
