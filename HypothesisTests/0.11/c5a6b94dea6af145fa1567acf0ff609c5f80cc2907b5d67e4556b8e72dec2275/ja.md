```
DurbinWatsonTest(X::AbstractArray, e::AbstractVector; p_compute::Symbol = :ndep)
```

回帰モデルの残差における系列相関のためのダービン-ワトソン検定を計算します。

`X` は元の回帰モデルからの回帰変数の行列で、`e` は残差のベクトルです。`X` に遅延従属変数が含まれている場合、ダービン-ワトソン検定は無効であることに注意してください。検定統計量は次のように計算されます。

$$
DW = \frac{\sum_{t=2}^n (e_t - e_{t-1})^2}{\sum_{t=1}^n e_t^2}
$$

ここで、`n` は観測数です。

デフォルトでは、p値を計算するためのアプローチの選択はサンプルサイズに依存します（`p_compute=:ndep`）。小さなサンプル（n<100）の場合、パンのアルゴリズム（Farebrother, 1980）が使用されます。大きなサンプルの場合、正規近似が使用されます（Durbin and Watson, 1950）。常にパンのアルゴリズムを使用するには、`p_compute=:exact` を設定します。`p_compute=:approx` は常に正規近似を使用します。

デフォルトは、正または負の系列相関の対立仮説に対する両側p値です。一側p値は、`pvalue(x::DurbinWatsonTest; tail=)` を呼び出すことで要求でき、オプション `:left`（負の系列相関）および `:right`（正の系列相関）を指定できます。

# 参考文献

  * J. Durbin and G. S. Watson, 1951, "Testing for Serial Correlation in Least Squares Regression: II", Biometrika, Vol. 38, No. 1/2, pp. 159-177, [http://www.jstor.org/stable/2332325](http://www.jstor.org/stable/2332325).
  * J. Durbin and G. S. Watson, 1950, "Testing for Serial Correlation in Least Squares Regression: I", Biometrika, Vol. 37, No. 3/4, pp. 409-428, [http://www.jstor.org/stable/2332391](http://www.jstor.org/stable/2332391).
  * R. W. Farebrother, 1980, "Algorithm AS 153: Pan's Procedure for the Tail Probabilities of the Durbin-Watson Statistic", Journal of the Royal Statistical Society, Series C (Applied Statistics), Vol. 29, No. 2, pp. 224-227, [http://www.jstor.org/stable/2986316](http://www.jstor.org/stable/2986316).

# 外部リンク

  * [ウィキペディアのダービン-ワトソン検定](https://en.wikipedia.org/wiki/Durbin–Watson_statistic)

```
