```
anova_lfe(f::FormulaTerm, tbl, vcov::CovarianceEstimator = Vcov.simple(); 
        test::Type{<: GoodnessOfFit} = FTest, <keyword arguments>)
anova_lfe(test::Type{<: GoodnessOfFit}, f::FormulaTerm, tbl, vcov::CovarianceEstimator = Vcov.simple(); <keyword arguments>)
```

固定効果線形回帰のためのANOVA。

  * `vcov`: 共分散行列の推定量。
  * `type`: anovaのタイプ (1 , 2 または 3)。デフォルト値は1です。

`anova_lfe`は`FixedEffectModel`を生成します。
