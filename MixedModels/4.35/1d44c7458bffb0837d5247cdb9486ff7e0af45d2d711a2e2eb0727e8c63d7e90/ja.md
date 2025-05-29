```
likelihoodratiotest(m::MixedModel...)
likelihoodratiotest(m0::LinearModel, m::MixedModel...)
likelihoodratiotest(m0::GeneralizedLinearModel, m::MixedModel...)
likelihoodratiotest(m0::TableRegressionModel{LinearModel}, m::MixedModel...)
likelihoodratiotest(m0::TableRegressionModel{GeneralizedLinearModel}, m::MixedModel...)
```

ネストされたモデルのセットに適用される尤度比検定。

!!! note
    モデルのネストはチェックされません。これを確認するのはユーザーの責任です。これは、特にランダム効果の仕様において、混合モデルのネストが明白でない場合があるため、`StatsModels.lrtest`とは異なります。


!!! note
    混合モデルと非混合モデルの比較において、非混合モデルの偏差は -2 対数尤度と見なされます。つまり、完全に飽和したモデルの加法定数を省略します。これは、混合モデルの偏差の計算と一致しています。


この機能は、将来的に `StatsModels.lrtest` に取って代わられる可能性があります。
