```
stocks_aggregates_bars(opts::PolyOpts, stocksTicker::AbstractString;
                    multiplier=1, timespan="day", from="2020-10-14", to="2020-10-14",
                    adjusted=true, sort="asc", limit=120, kwargs...)
```

指定された日付範囲内の株式の集約バーをカスタム時間ウィンドウサイズで取得します。たとえば、timespan = ‘minute’ および multiplier = ‘5’ の場合、5分間のバーが返されます。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用される PolyOpts オブジェクト。
  * stocksTicker::AbstractString: 株式/株のティッカーシンボル。
  * multiplier::Int: タイムスパンの乗数のサイズ。
  * timespan::AbstractString: 時間ウィンドウのサイズ。
  * from::AbstractString: 集約時間ウィンドウの開始。
  * to::AbstractString: 集約時間ウィンドウの終了。
  * adjusted::Bool: 結果が分割に対して調整されているかどうか。デフォルトでは、結果は調整されています。これを false に設定すると、分割に対して調整されていない結果が得られます。
  * sort::AbstractString: タイムスタンプで結果をソートします。asc は結果を昇順（古いものが上）で返し、desc は結果を降順（新しいものが上）で返します。
  * limit::Int: 集約結果を作成するためにクエリされる基本集約の数を制限します。最大 50000、デフォルト 120。
  * kwargs::AbstractString: その他の追加引数。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_aggregates_bars(opts, "AAPL", multiplier=5, timespan="minute", from="2017-01-01", to="2017-01-01")
```

# 戻り値

  * JSON3.Array または JSON3.Array の指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*aggs_ticker**stocksTicker**range**multiplier___timespan___from___to**anchor を参照してください。
