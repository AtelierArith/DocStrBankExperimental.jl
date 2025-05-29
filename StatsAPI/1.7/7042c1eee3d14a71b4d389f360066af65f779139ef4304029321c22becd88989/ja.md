```
loglikelihood(model::StatisticalModel)
loglikelihood(model::StatisticalModel, observation)
```

モデルの対数尤度を返します。

`observation` 引数がある場合、`observation` がモデルの対数尤度への寄与を返します。

`observation` が `Colon` の場合、モデルの対数尤度への各観測の寄与のベクトルを返します。言い換えれば、これは点ごとの対数尤度寄与のベクトルです。

一般に、`sum(loglikehood(model, :)) == loglikelihood(model)` です。
