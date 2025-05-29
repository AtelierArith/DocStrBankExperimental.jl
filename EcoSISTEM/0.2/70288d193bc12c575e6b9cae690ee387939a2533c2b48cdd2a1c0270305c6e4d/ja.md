```
raingradAE(min::Unitful.Temperature{Float64},
  max::Unitful.Temperature{Float64},
  dimension::Tuple{Int64, Int64}, maxbud::Float64,
  area::Unitful.Area{Float64}, rate::Quantity{Float64, typeof(𝚯*𝐓^-1)},
  active::Matrix{Bool})
```

雨勾配 `ContinuousHab`、`SimpleBudget` タイプの非生物環境を作成する関数。`min` と `max` の降雨量を指定すると、下部の最小値から上部の最大値までの勾配が生成されます。`dimension` の寸法と指定された面積 `area` を持つ `ContinuousHab` 環境が作成されます。また、最大予算値 `maxbud` で満たされた `SimpleBudget` タイプも作成されます。降雨量の変化率はパラメータ `rate` を使用して指定されます。アクティブなグリッドセルの Bool 行列 `active` が含まれている場合はこれが使用され、そうでない場合はすべてのグリッドセルがアクティブなものが作成されます。
