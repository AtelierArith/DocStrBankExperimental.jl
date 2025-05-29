tickers(opts::PolyOpts, search::AbstractString;         active=true, sort="ticker", order="asc", limit=10, kwargs...)

Polygon.ioによってサポートされているすべてのティッカーシンボルをクエリします。このAPIには現在、株式/株、暗号通貨、および外国為替が含まれています。

# 引数

  * opts::PolyOpts - リクエストを構成するために使用されるPolyOptsオブジェクト。
  * search::AbstractString - ティッカーおよび/または会社名内の用語を検索します。
  * active::Boolean - 返されるティッカーがクエリされた日付でアクティブに取引されているべきかどうかを指定します。デフォルトはtrueです。
  * sort::String - 結果をソートするフィールド。デフォルトはティッカーです。検索クエリパラメータが存在する場合、ソートは無視され、結果は関連性によって順序付けられます。
  * order::String - 結果をソートする順序。デフォルトはasc（昇順）です。
  * limit::Integer - レスポンスのサイズを制限します。デフォルトは100で、最大は1000です。クエリが最大制限を超える場合、次のページの結果を取得したい場合は、next_urlレスポンス属性を参照してください。
  * kwargs::Dict - 追加のクエリパラメータ。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> tickers(opts, "bitcoin")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * レスポンス属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v3*reference*tickers*anchorを参照してください。
