```
stock_dividends(opts::PolyOpts, stocksTicker::AbstractString)
```

株式の過去の配当金のリストを取得し、関連する日付と配当金の金額を含みます。

# 引数

  * opts::PolyOpts - リクエストを構成するために使用されるPolyOptsオブジェクト。
  * stocksTicker::AbstractString - 株式/株のティッカーシンボル。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stock_dividends(opts, "AAPL")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*reference_dividends**stocksTicker**anchorを参照してください。
