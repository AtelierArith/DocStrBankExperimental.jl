```
tempgradAE(min::Unitful.Temperature{Float64},
  max::Unitful.Temperature{Float64},
  dimension::Tuple{Int64, Int64}, maxbud::Float64,
  area::Unitful.Area{Float64}, rate::Quantity{Float64, typeof(𝚯*𝐓^-1)},
  active::Matrix{Bool})
```

温度勾配 `ContinuousHab`、`SimpleBudget` タイプの非生物環境を作成する関数。`min` と `max` の温度が与えられると、底部の最小値から上部の最大値までの勾配を生成します。`dimension` の寸法と指定された面積 `area` を持つ `ContinuousHab` 環境を作成します。また、最大予算値 `maxbud` で満たされた `SimpleBudget` タイプも作成します。温度変化の割合はパラメータ `rate` を使用して指定されます。アクティブなグリッドセルの Bool 行列 `active` が含まれている場合はこれが使用され、そうでない場合はすべてのグリッドセルがアクティブなものが作成されます。
