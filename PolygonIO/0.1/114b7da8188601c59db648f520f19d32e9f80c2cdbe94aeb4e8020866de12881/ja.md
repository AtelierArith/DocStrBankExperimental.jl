```
crypto_snapshot_ticker(opts::PolyOpts, ticker="X:BTCUSD")
```

現在の分、日、および前日の集計、さらに単一の取引された暗号通貨シンボルの最後の取引と引用を取得します。注意: スナップショットデータは午前12時ESTにクリアされ、取引所からデータが受信されるとともに更新されます。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * ticker: スナップショットのティッカー。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> crypto_snapshot_ticker(opts, "X:BTCUSD")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*snapshot*locale*global*markets*crypto_tickers**ticker**anchor を参照してください。
