```
ticker_news(opts::PolyOpts, ticker::AbstractString;
            published_utc_gte="2021-04-26", limit=10,
            order="descending", sort="published_utc",kwargs...)
```

株式ティッカーシンボルに関連する最新のニュース記事を取得し、記事の要約と元のソースへのリンクを含みます。

# 引数

  * opts::PolyOpts - リクエストを構成するために使用されるPolyOptsオブジェクト。
  * ticker::AbstractString - ティッカーシンボル。このフィールドがこの値に等しい結果を返します。
  * published*utc*gte::AbstractString - このフィールドがこの値以上の結果を返します。
  * limit::Integer - 応答のサイズを制限します。デフォルトは100、最大は1000です。クエリが最大制限を超える結果を返す場合、次のページの結果を取得するには、next_url応答属性を参照してください。
  * order::String - 結果を昇順または降順に並べます。
  * sort::String - 結果を並べ替えるフィールドキー。
  * kwargs::Dict - 追加のクエリパラメータ

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> ticker_news(opts, "AAPL", limit=5)
```

# 戻り値

  * JSON3.Arrayまたは指定されたJSON3.Arrayの表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*reference*news*anchor を参照してください。
