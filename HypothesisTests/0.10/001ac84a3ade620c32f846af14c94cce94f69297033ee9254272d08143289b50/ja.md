```
JarqueBeraTest(y::AbstractVector; adjusted::Bool=false)
```

`adjusted`が`false`の場合、実数値ベクトル`y`が正規分布しているという帰無仮説を検定するために、Jarque-Bera統計量を計算します。

カイ二乗分布による近似はうまく機能せず、収束の速度が遅いことに注意してください。小さなサンプルでは、テストは名目水準が約3%まで過大であり、より大きな名目水準では過小になる傾向があります（Mantalos, 2010）。

`adjusted`が`true`の場合、実数値ベクトル`y`が正規分布しているという帰無仮説を検定するために、調整ラグランジュ乗数統計量を計算します。

調整ラグランジュ乗数の使用は、小規模および中規模のサンプルサイズに対してJarque-Beraよりも好ましく、Jarque-Beraテストへの修正です（Urzua, 1996）。

# 参考文献

  * Panagiotis Mantalos, 2011, "The three different measures of the sample skewness and kurtosis and the effects to the Jarque-Bera test for normality", International Journal of Computational Economics and Econometrics, Vol. 2, No. 1, [link](http://dx.doi.org/10.1504/IJCEE.2011.040576).
  * Carlos M. Urzúa, "On the correct use of omnibus tests for normality", Economics Letters, Volume 53, Issue 3, [link](https://doi.org/10.1016/S0165-1765(96)00923-8).

# 外部リンク

  * [Jarque-Bera test on Wikipedia](https://en.wikipedia.org/wiki/Jarque–Bera_test)

```
