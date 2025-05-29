```
propci(x::Int, n::Int; level = 0.95, method = :default)
```

比率信頼区間。

`method`:

  * `:wilson` | `:default` - 単一比率のウィルソン信頼区間 (CI) (ウィルソン, 1927);
  * `:wilsoncc` - 連続補正 (CC) を伴うウィルソンの CI;
  * `:cp` - クラッパー-ピアソンの正確な CI (クラッパー＆ピアソン, 1934);
  * `:blaker` - 離散分布のためのブレイカーの正確な CI (ブレイカー, 2000);
  * `:soc` - SOC: 二次補正された CI;
  * `:arc` - アークサイン CI;
  * `:wald` - CCなしのワルド CI;
  * `:waldcc` - CC (1/2/n) を伴うワルド CI;
  * `:ac` - アグレスティ-クール;
  * `:jeffrey` - ジェフリーズ区間 (ブラウン et al, 2001)。

参考文献:

  * ウィルソン, E.B. (1927) Probable inference, the law of succession, and statistical inference J. Amer.Stat. Assoc 22, 209–212;
  * クラッパー, C. とピアソン, E.S. (1934) The use of confidence or fiducial limits illustrated in the case of the binomial. Biometrika 26, 404–413;
  * アグレスティ A. とクール B.A. (1998) Approximate is better than "exact" for interval estimation of binomial proportions. American Statistician, 52, pp. 119-126.
  * ニューカム, R. G. (1998) Two-sided confidence intervals for the single proportion: comparison of seven methods, Statistics in Medicine, 17:857-872 https://pubmed.ncbi.nlm.nih.gov/16206245/
  * ブレイカー, H. (2000). Confidence curves and improved exact confidence intervals for discrete distributions, Canadian Journal of Statistics 28 (4), 783–798;
  * ピレス, アナ & アマド, コンセイサン. (2008). Interval Estimators for a Binomial Proportion: Comparison of Twenty Methods. REVSTAT. 6. 10.57805/revstat.v6i2.63.
