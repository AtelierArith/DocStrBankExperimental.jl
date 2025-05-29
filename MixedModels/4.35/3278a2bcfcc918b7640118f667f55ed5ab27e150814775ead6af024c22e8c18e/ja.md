```
dof_residual(m::MixedModel)
```

モデルの残差自由度を返します。

!!! note
    混合効果モデルの残差自由度は部分プーリングのため明確に定義されていません。古典的な `nobs(m) - dof(m)` はランダム効果によって与えられる追加の自由度を捉えられませんが、`nobs(m) - nranef(m)` はランダム効果によって与えられる自由度を過大評価します。`nobs(m) - sum(leverage(m))` は各観測値の相対的影響に基づいて良いバランスを提供しますが、大規模なモデルでは計算コストが高くなります。この問題は、$F$-テストのための分母自由度の適切な扱いに関する[長年の議論](https://bbolker.github.io/mixedmodels-misc/glmmFAQ.html#why-doesnt-lme4-display-denominator-degrees-of-freedomp-values-what-other-options-do-i-have)にも根本的に関連しています。将来的には、MixedModels.jlがユーザーが使用する計算を選択できる追加の方法を提供するかもしれません。


!!! warning
    現在、残差自由度は `nobs(m) - dof(m)` として計算されていますが、これは将来的に変更される可能性があり、混合効果モデルにおける残差自由度の標準的な定義が存在しないため、破壊的変更とは見なされません。

