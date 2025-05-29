```
market_status(opts::PolyOpts)
```

取引所と全体の金融市場の現在の取引状況を取得します。

# 引数

  * opts::PolyOpts - リクエストを構成するために使用されるPolyOptsオブジェクト。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> market_status(opts)
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v1*marketstatus*now*anchor を参照してください。
