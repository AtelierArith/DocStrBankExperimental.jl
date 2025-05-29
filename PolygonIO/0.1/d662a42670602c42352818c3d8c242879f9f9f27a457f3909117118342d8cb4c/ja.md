```
ticker_details(opts::PolyOpts, stocksTicker::AbstractString)
```

ティッカーシンボルの会社/エンティティの詳細を取得します。これにより、名前、セクター、取引所、ロゴ、類似企業などの情報を含むエンティティの一般的な概要が提供されます。

# 引数

  * opts::PolyOpts - リクエストを構成するために使用されるPolyOptsオブジェクト。
  * stocksTicker::AbstractString - 株式/株式のティッカーシンボル。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> ticker_details(opts, "AAPL")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントについては、https://polygon.io/docs/get*v2*reference*ticker*details_anchor を参照してください。
