```
stock_splits(opts::PolyOpts, stocksTicker::AbstractString)
```

ティッカーシンボルの過去の株式分割のリストを取得します。これには、株式分割の実行日と支払日、および分割比率が含まれます。

# 引数

  * opts::PolyOpts - リクエストを構成するために使用されるPolyOptsオブジェクト。
  * stocksTicker::AbstractString - 株式/株式のティッカーシンボル。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stock_splits(opts, "AAPL")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントについては、https://polygon.io/docs/get*v2*reference_splits**stocksTicker**anchor を参照してください。
