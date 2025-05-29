```
confint(test::PowerDivergenceTest; level = 0.95, tail = :both, method = :auto)
```

多項分布の比率に対して、次のいずれかの方法を使用してカバレッジ `level` の信頼区間を計算します。`method` の可能な値は次のとおりです。

  * `:auto` (デフォルト): 期待されるセルの最小カウントが100を超える場合はQuesenberry-Hurst区間が使用され、それ以外の場合はSison-Glazが使用されます。
  * `:sison_glaz`: Sison-Glaz区間
  * `:bootstrap`: ブートストラップ区間
  * `:quesenberry_hurst`: Quesenberry-Hurst区間
  * `:gold`: ゴールド区間（漸近的同時区間）

# 参考文献

  * Agresti, Alan. Categorical Data Analysis, 3rd Edition. Wiley, 2013.
  * Sison, C.P and Glaz, J. Simultaneous confidence intervals and sample size determination for multinomial proportions. Journal of the American Statistical Association, 90:366-369, 1995.
  * Quesensberry, C.P. and Hurst, D.C. Large Sample Simultaneous Confidence Intervals for Multinational Proportions. Technometrics, 6:191-195, 1964.
  * Gold, R. Z. Tests Auxiliary to $χ^2$ Tests in a Markov Chain. Annals of Mathematical Statistics, 30:56-74, 1963.
