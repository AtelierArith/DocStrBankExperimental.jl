```
updateone!(b::Booster, data; round_number=getnrounds(b)+1,
           watchlist=Dict("train"=>data), update_feature_names=false
          )
```

ブースター `b` を使用してデータ `data` に対して1ラウンドの勾配ブースティングを実行します。 `data` は [`DMatrix`](@ref) コンストラクタによって受け入れられる任意のオブジェクトです。 `round_number` は現在のラウンドの番号であり、ログのみに使用されます。 情報ログは、`watchlist` にあるトレーニングセットのために印刷されます。 キーは、ログ記録の目的でそのデータセットの名前を示します。
