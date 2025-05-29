```
stock_financials(opts::PolyOpts, stocksTicker::AbstractString; limit=5, kwargs...)
```

株式ティッカーの過去の財務データを取得します。

# 引数

  * opts::PolyOpts - リクエストを構成するために使用されるPolyOptsオブジェクト。
  * stocksTicker::AbstractString - 株式/株のティッカーシンボル。
  * limit::Integer - 結果の数を制限します。
  * kwargs::Any: Polygon IO APIに渡す追加の引数のリスト。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stock_financials(opts, "AAPL", limit=5)
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*reference*financials*anchor を参照してください。
