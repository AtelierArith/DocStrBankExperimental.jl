```
forex_snapshot_ticker(opts::PolyOpts, forexTicker="C:EURUSD")
```

現在の分、日、および前日の集計、さらに単一の取引通貨シンボルの最後の取引と引用を取得します。注意: スナップショットデータは東部標準時の午前12時にクリアされ、取引所からデータが受信されるとともに補充されます。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * forexTicker: 外国為替ティッカー。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> forex_snapshot_ticker(opts, "C:EURUSD")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*snapshot*locale*global*markets*forex_tickers**ticker**anchor を参照してください。
