```
anova_lfe(f::FormulaTerm, tbl, vcov::CovarianceEstimator = Vcov.simple(); 
        test::Type{<: GoodnessOfFit} = FTest, <keyword arguments>)
anova_lfe(test::Type{<: GoodnessOfFit}, f::FormulaTerm, tbl, vcov::CovarianceEstimator = Vcov.simple(); <keyword arguments>)
```

ANOVA for fixed-effect linear regression.

  * `vcov`: estimator of covariance matrix.
  * `type`: type of anova (1 , 2 or 3). Default value is 1.

`anova_lfe` generates a `FixedEffectModel`.
