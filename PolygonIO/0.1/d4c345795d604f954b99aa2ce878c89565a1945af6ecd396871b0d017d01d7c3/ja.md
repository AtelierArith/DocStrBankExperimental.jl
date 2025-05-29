```
ticker_details_vX(opts::PolyOpts, ticker::AbstractString, date::AbstractString)
```

Polygon.ioがサポートする単一のティッカーを取得します。この応答には、ティッカーおよびその背後にある会社に関する詳細情報が含まれます。

# 引数

  * opts::PolyOpts - リクエストを構成するために使用されるPolyOptsオブジェクト。
  * ticker::AbstractString - 資産のティッカーシンボル。
  * date::AbstractString - 特定の日付におけるティッカーに関する情報を取得するためのポイントを指定します。SEC提出書類から情報を取得する際には、この日付をSEC提出書類の報告期間終了日と比較します。

例えば、AAPLが2019-07-31に提出したSEC提出書類を考えてみてください。報告期間終了日は2019-06-29です。これは、提出書類が2019-07-31に提出されたが、2019-06-29の情報に基づいて作成されたことを意味します。2019-06-29にAAPLの詳細を照会すると、ティッカーの詳細にはSEC提出書類からの情報が含まれます。デフォルトでは、最も最近の利用可能な日付になります。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> ticker_details_vX(opts, "AAPL", "2017-01-01")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*vX*reference_tickers**ticker**anchorを参照してください。
