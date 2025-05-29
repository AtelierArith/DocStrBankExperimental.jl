```
forex_snapshot_all_tickers(opts::PolyOpts; kwargs...)
```

現在の分、日、および前日の集計、ならびにすべての取引された外国為替シンボルの最後の取引と引用を取得します。注意: スナップショットデータは午前12時ESTにクリアされ、取引所からデータが受信されるとともにポピュレートされます。これは午前4時ESTに早くも発生する可能性があります。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * kwargs: PolyOptsに渡すキーワード引数。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> forex_snapshot_all_tickers(opts)
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*snapshot*locale*global*markets*forex*tickers*anchor を参照してください。

```
