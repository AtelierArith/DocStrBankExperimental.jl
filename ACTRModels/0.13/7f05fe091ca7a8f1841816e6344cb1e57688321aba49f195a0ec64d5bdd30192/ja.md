```
posterior_predictive(model, chain, n_samples::Int, f=x -> x)
```

事後予測分布を返し、オプションで各複製のサンプルに関数を適用します

  * `model`: モデルのデータ生成関数
  * `chain`: MCMCChainsチェーンオブジェクト
  * `n_samples`: サンプルの数
  * `f`: 事後予測分布からの各サンプルに適用される関数
