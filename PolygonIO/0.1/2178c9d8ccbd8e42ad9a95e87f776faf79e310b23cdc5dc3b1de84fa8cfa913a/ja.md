```
crypto_aggregates_bars(opts::PolyOpts, cryptoTicker="X:BTCUSD", multiplier=1, timespan="day", from="2020-10-14", to="2020-10-14";
                       adjusted=true, sort="asc", limit=120, kwargs...)
```

指定された日付範囲内で、カスタム時間ウィンドウサイズの暗号通貨ペアの集約バーを取得します。たとえば、timespan = ‘minute’ および multiplier = ‘5’ の場合、5分間隔のバーが返されます。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * cryptoTicker: 通貨ペアのティッカーシンボル。
  * multiplier: タイムスパンの乗数のサイズ。
  * timespan: タイムスパンの乗数のサイズ。
  * from: 集約時間ウィンドウの開始。
  * to: 集約時間ウィンドウの終了。
  * adjusted: 結果がスプリットに対して調整されているかどうか。デフォルトでは、結果は調整されています。これをfalseに設定すると、スプリットに対して調整されていない結果が得られます。
  * sort: タイムスタンプで結果をソートします。ascは結果を昇順（古いものが上）で返し、descは結果を降順（新しいものが上）で返します。
  * limit: 集約結果を作成するためにクエリされる基本集約の数を制限します。最大50000、デフォルトは120です。
  * kwargs: リクエストに渡す追加の引数。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> crypto_aggregates_bars(opts, "X:BTCUSD", 5, "minute", "2020-10-14", "2020-10-14")
```

# 戻り値

  * JSON3.Array または JSON3.Array の指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*aggs_ticker**cryptoTicker**range**multiplier___timespan___from___to**anchor を参照してください。
