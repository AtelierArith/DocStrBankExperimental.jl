```
stocks_snapshot_gainers_losers(opts::PolyOpts, direction="losers")
```

現在の株式/株式市場におけるトップ20の上昇銘柄または下落銘柄を取得します。トップ上昇銘柄は、前日の終値から最も高い割合で価格が上昇したティッカーです。トップ下落銘柄は、前日の終値から最も高い割合で価格が下落したティッカーです。注意: スナップショットデータは、東部標準時の午前12時にクリアされ、取引所からデータが受信されるとともに更新されます。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * direction::AbstractString: 返すスナップショット結果の方向。方向は「gainers」または「losers」とすることができます。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_snapshot_gainers_losers(opts, "losers")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*snapshot*locale*us*markets*stocks**direction**anchorを参照してください。
