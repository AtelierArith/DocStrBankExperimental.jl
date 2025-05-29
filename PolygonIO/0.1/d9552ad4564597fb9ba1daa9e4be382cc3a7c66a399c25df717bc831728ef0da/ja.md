```
stocks_previous_close(opts::PolyOpts, stocksTicker::AbstractString; adjusted=true)
```

指定された株式ティッカーの前日の始値、高値、安値、終値（OHLC）を取得します。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * stocksTicker::AbstractString: 株式/株式のティッカーシンボル。
  * adjusted::Bool: 結果が株式分割に対して調整されているかどうか。デフォルトでは、結果は調整されています。これをfalseに設定すると、株式分割に対して調整されていない結果が得られます。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_previous_close(opts, "AAPL")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*aggs*ticker**stocksTicker**prev*anchor を参照してください。
