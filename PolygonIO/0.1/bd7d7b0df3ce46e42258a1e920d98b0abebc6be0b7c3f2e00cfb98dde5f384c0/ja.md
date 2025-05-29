```
markets(opts::PolyOpts)
```

Polygon.ioによって現在サポートされている市場のリストを取得します。

# 引数

  * opts::PolyOpts - リクエストを構成するために使用されるPolyOptsオブジェクト。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> markets(opts)
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*reference*markets*anchor を参照してください。
