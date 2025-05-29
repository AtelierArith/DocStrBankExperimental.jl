```
stocks_snapshot_ticker(opts::PolyOpts, stocksTicker::AbstractString)
```

現在の分、日、および前日の合計、さらに単一の取引株ティッカーの最終取引と引用を取得します。注意: スナップショットデータは午前12時ESTにクリアされ、取引所からデータが受信されるとともにポピュレートされます。これは午前4時ESTに早くも発生する可能性があります。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * stocksTicker::AbstractString: 株式/株式のティッカーシンボル。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_snapshot_ticker(opts, "AAPL")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*snapshot*locale*us*markets*stocks_tickers**stocksTicker**anchorを参照してください。

```
