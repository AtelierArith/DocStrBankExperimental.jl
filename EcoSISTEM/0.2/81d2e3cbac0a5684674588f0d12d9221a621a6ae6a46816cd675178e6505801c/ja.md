```
simplehabitatAE(val::Union{Float64, Unitful.Quantity{Float64}},
    dimension::Tuple{Int64, Int64}, maxbud::Float64, area::Unitful.Area{Float64},
    active::Matrix{Bool})
```

`ContinuousHab`、`SimpleBudget` タイプの非生物環境を作成する関数です。指定された値 `val`、次元 (`dimension`) および指定された面積 (`area`) で満たされた `ContinuousHab` を作成します。また、最大予算値 (`maxbud`) で満たされた `SimpleBudget` タイプも作成します。温度変化の速度はパラメータ `rate` を使用して指定されます。アクティブなグリッドセルの Bool 行列 `active` が含まれている場合はこれが使用され、そうでない場合はすべてのグリッドセルがアクティブなものが作成されます。
