```
stocks_daily_open_close(opts::PolyOpts, stocksTicker::AbstractString, date::AbstractString; adjusted=true)
```

特定の日付における株式シンボルの始値、終値、アフターアワーズ価格を取得します。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * stocksTicker::AbstractString: 株式/株式のティッカーシンボル。
  * date::AbstractString: リクエストされた始値/終値の日付（フォーマットはYYYY-MM-DD）。
  * adjusted::Bool: 結果が株式分割に対して調整されているかどうか。デフォルトでは、結果は調整されています。株式分割に対して調整されていない結果を取得するには、これをfalseに設定します。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_daily_open_close(opts, "AAPL", "2017-01-01")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v1*open-close**stocksTicker___date**anchorを参照してください。
