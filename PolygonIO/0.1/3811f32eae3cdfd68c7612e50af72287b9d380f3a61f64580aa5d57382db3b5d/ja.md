```
stocks_grouped_daily_bars(opts::PolyOpts, date::AbstractString; adjusted=true)
```

株式/株式市場全体の毎日の始値、高値、安値、終値（OHLC）を取得します。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * date::AbstractString: 集約ウィンドウの開始日。
  * adjusted::Bool: 結果が株式分割に対して調整されているかどうか。デフォルトでは、結果は調整されています。株式分割に対して調整されていない結果を取得するには、これをfalseに設定します。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_grouped_daily_bars(opts, "2017-01-01")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*aggs*grouped*locale*us*market_stocks**date**anchorを参照してください。
