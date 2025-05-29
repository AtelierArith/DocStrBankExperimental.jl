```
CorrelationTest(x, y)
```

ベクトル `x` と `y` の相関がゼロであるという仮説に対する t 検定を実行します。すなわち、$\text{Cor}(x,y) = 0$ です。

```
CorrelationTest(x, y, Z)
```

行列 `Z` を与えた場合のベクトル `x` と `y` の部分相関がゼロであるという仮説に対する t 検定を実行します。すなわち、$\text{Cor}(x,y|Z=z) = 0$ です。

t 検定のための `pvalue` を実装します。Fisher の $z$-変換に基づく近似信頼区間を使用して `confint` を実装します。

`partialcor` from StatsBase も参照してください。

# 外部リソース

  * [ウィキペディアの部分相関](https://en.wikipedia.org/wiki/Partial_correlation#As_conditional_independence_test)（信頼区間の構築について）
  * [ウィキペディアのピアソン相関係数に関するセクション検定](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient#Testing_using_Student's_t-distribution)
  * [K.J. Levy と S.C. Narula (1978): 部分相関に関する仮説の検定: 一部の方法と議論。国際統計レビュー 46(2).](https://www.jstor.org/stable/1402814)
