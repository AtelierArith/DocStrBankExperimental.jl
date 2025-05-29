```
stocks_last_quote_symbol(opts::PolyOpts, stocksTicker::AbstractString)
```

指定された株式の最新のNBBO（見積もり）ティックを取得します。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * stocksTicker::AbstractString: 株式/株のティッカーシンボル。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_last_quote_symbol(opts, "AAPL")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*last_nbbo**stocksTicker**anchorを参照してください。
