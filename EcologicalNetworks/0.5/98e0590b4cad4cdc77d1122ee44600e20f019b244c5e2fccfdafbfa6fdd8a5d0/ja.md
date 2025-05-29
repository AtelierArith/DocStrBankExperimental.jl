```
overlap(N::T; dims=dims::Union{Nothing,Integer}=nothing) where {T <: BipartiteNetwork}
```

二部ネットワークのオーバーラップグラフを返します。`dims`キーワード引数は`1`（デフォルト；トップレベルの種間のオーバーラップ）または`2`（ボトムレベルの種間のオーバーラップ）に設定できます。出力形式については`?overlap`のドキュメントを参照してください。
