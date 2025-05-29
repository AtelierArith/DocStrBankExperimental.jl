```
peakedgradAE(minT::Unitful.Temperature{Float64},
   maxT::Unitful.Temperature{Float64},
   dimension::Tuple{Int64, Int64}, maxbud::Unitful.Quantity{Float64},
   area::Unitful.Area{Float64}, rate::Quantity{Float64, 𝚯*𝐓^-1},
   active::Matrix{Bool})
```

温度勾配 `ContinuousHab`、`SimpleBudget` タイプの非生物環境を作成する関数。`min` および `max` 温度を指定すると、上部と下部で最小値から始まり、中央で最大値に達する勾配が生成されます。指定された面積 `area` と次元 `dimension` を持つ `ContinuousHab` 環境が作成されます。また、最大予算値 `maxbud` で満たされた `SimpleBudget` タイプも作成されます。温度変化の割合はパラメータ `rate` を使用して指定されます。アクティブなグリッドセルのブール行列 `active` が含まれている場合はこれが使用され、そうでない場合はすべてのグリッドセルがアクティブなものが作成されます。
