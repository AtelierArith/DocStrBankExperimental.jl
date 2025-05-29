```
sampledist(params::PriorHyperparamsList, type::String, numsamples = 1)::Vector{Float64}
```

`params`にカプセル化された距離の事前予測分布から、長さ`numsamples`のサンプルのベクトルを生成します。`type`は`"intercluster"`または`"intracluster"`のいずれかでなければなりません。
