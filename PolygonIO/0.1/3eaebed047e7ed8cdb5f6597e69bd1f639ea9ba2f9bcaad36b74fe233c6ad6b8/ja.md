```
condition_mappings(opts::PolyOpts, tickertype="trades")
```

取引および引用に関する条件の統一された数値マッピングを取得します。各フィード/取引所は、条件を識別するために独自のコードセットを使用しているため、同じ条件がデータの発信者によって異なるコードを持つ場合があります。Polygon.ioは、フィード/取引所全体で条件を一貫して識別できるように独自のマッピングを定義しています。

# 引数

  * opts::PolyOpts - リクエストを構成するために使用されるPolyOptsオブジェクト。
  * tickertype::AbstractString - マッピングを返すためのティックの種類。 "trades"または"quotes"のいずれかでなければなりません。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> condition_mappings(opts, "trades")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントについては、https://polygon.io/docs/get*v1*condition*mappings*anchor を参照してください。
