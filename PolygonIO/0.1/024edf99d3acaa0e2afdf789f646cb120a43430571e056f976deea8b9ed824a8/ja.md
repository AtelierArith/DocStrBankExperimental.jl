```
stocks_trades(opts::PolyOpts, ticker::AbstractString, date::AbstractString; limit=10, reverse=true, kwargs...)
```

指定された日付の特定のティッカーシンボルの株式取引を取得します。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * ticker::AbstractString: 取引を希望するティッカーシンボル。
  * date::AbstractString: YYYY-MM-DD形式で取得する取引の日付。
  * limit::Int: 応答のサイズを制限、最大50000、デフォルトは10。
  * reverse::Boolean: 結果の順序を逆にする。
  * kwargs::Any: Polygon IO APIに渡す追加の引数のリスト。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_trades(opts, "AAPL", "2017-01-01")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*ticks*stocks*trades**ticker___date**anchorを参照してください。
