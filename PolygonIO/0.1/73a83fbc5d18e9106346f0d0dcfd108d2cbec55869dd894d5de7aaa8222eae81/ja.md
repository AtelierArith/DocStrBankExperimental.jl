```
forex_previous_close(opts::PolyOpts, forexTicker="C:EURUSD"; adjusted=true)
```

指定された外国為替ペアの前日の始値、高値、安値、終値（OHLC）を取得します。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * forexTicker: 通貨ペアのティッカーシンボル。
  * adjusted: 結果がスプリットに対して調整されているかどうか。デフォルトでは、結果は調整されています。これをfalseに設定すると、スプリットに対して調整されていない結果が得られます。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> forex_previous_close(opts, "C:EURUSD")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*aggs*ticker**forexTicker**prev*anchor を参照してください。
