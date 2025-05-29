```
anova_glm(X, y, d::UnivariateDistribution, l::Link = canonicallink(d); 
        test::Type{<: GoodnessOfFit} = canonicalgoodnessoffit(d), <keyword arguments>)

anova_glm(test::Type{<: GoodnessOfFit}, X, y, d::UnivariateDistribution, l::Link = canonicallink(d); <keyword arguments>)

anova(test::Type{<: GoodnessOfFit}, X, y, d::UnivariateDistribution, l::Link = canonicallink(d); <keyword arguments>)
```

一般化線形モデルのANOVA。

# 引数

  * `X` と `y` は `Matrix` と `Vector` または `Formula` と `Tables.jl` 互換のデータであることができます。
  * `d`: `GLM.UnivariateDistribution`。
  * `l`: `GLM.Link`
  * `test`: 分布関数に基づく適合度のための検定統計量。`canonicalgoodnessoffit`を参照してください。

他のキーワード引数については、`fit`を参照してください。
