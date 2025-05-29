```
stocks_snapshot_all_tickers(opts::PolyOpts, tickers::AbstractString)
```

現在の分、日、および前日の集計、ならびにすべての取引された株式シンボルの最後の取引と引用を取得します。注意: スナップショットデータは東部標準時の午前12時にクリアされ、取引所からデータが受信されるとともに補充されます。これは東部標準時の午前4時に早くも発生する可能性があります。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * tickers::AbstractString: スナップショットを取得するためのティッカーのカンマ区切りリスト。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_snapshot(opts, "AAPL")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*snapshot*locale*us*markets*stocks*tickers*anchor を参照してください。
