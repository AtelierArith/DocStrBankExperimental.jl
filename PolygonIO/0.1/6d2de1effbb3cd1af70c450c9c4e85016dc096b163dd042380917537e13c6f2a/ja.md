```
crypto_snapshot_gainers_losers(opts::PolyOpts, direction="gainers")
```

暗号通貨市場における現在のトップ20のゲイナーまたはロサーを取得します。トップゲイナーは、前日の終値から最も高い割合で価格が上昇したティッカーです。トップロサーは、前日の終値から最も高い割合で価格が下落したティッカーです。注意: スナップショットデータは午前12時ESTにクリアされ、取引所からデータが受信されるとともに人口が増えます。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * direction: 返すスナップショット結果の方向。オプションは「gainers」または「losers」です。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> crypto_snapshot_gainers_losers(opts, "losers")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現。
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v2*snapshot*locale*global*markets*crypto**direction**anchorを参照してください。
