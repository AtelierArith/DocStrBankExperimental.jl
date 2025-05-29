```
crypto_exchanges(opts::PolyOpts)
```

Polygon.ioによってサポートされている暗号通貨取引所のリストを取得します。

# 引数

  * opts::PolyOpts - リクエストを構成するために使用されるPolyOptsオブジェクト。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> crypto_exchanges(opts)
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントについては、https://polygon.io/docs/get*v1*meta*crypto-exchanges*anchor を参照してください。
