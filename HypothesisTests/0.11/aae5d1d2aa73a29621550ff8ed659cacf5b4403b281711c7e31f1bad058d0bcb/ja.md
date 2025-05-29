```
ShapiroWilkTest(X::AbstractVector{<:Real},
                swc::AbstractVector{<:Real}=shapiro_wilk_coefs(length(X));
                sorted::Bool=issorted(X),
                censored::Integer=0)
```

ベクトル `X` のデータが正規分布から来ているという帰無仮説に対するシャピロ・ウィルク検定を実施します。

この実装は、Royston (1992) に基づいています。p値の計算は、サンプルサイズ `N = 3` の場合は正確であり、範囲 `4 ≤ N ≤ 11` および `12 ≤ N ≤ 5000` の場合には、p値のために2つの別々の近似が使用されます（Royston 1992）。

# キーワード引数

以下のキーワード引数を渡すことができます。

  * `sorted::Bool=issorted(X)`: サンプル `X` がすでにソートされていることを示します。
  * `censored::Integer=0`: `X` から最大のサンプルを検閲するため（いわゆる上側尾検閲）

実装: [`pvalue`](@ref)

!!! warning
    Royston (1993) によると、次のいずれかが当てはまる場合、（近似された）W統計量は正確ですが、返されるp値は信頼できない可能性があります：

      * サンプルサイズが大きい (`N > 2000`) または小さい (`N < 20`)
      * 検閲されたデータが多すぎる (`censored / N > 0.8`)


# 実装ノート

  * 現在の実装は、検閲されたデータのp値を実装していません。
  * 同じサイズのサンプルに対して複数のシャピロ・ウィルク検定を実施する場合、`swc = shapiro_wilk_coefs(length(X))` を一度構築し、`ShapiroWilkTest(X, swc)` を介してテストに渡す方が速いです。
  * 最大のパフォーマンスを得るためには、ソートされた `X` を渡し、`sorted=true` キーワード引数で示すべきです。

# 参考文献

Shapiro, S. S., & Wilk, M. B. (1965). An Analysis of Variance Test for Normality (Complete Samples). *Biometrika*, 52, 591–611. [doi:10.1093/BIOMET/52.3-4.591](https://doi.org/10.1093/BIOMET/52.3-4.591).

Royston, P. (1992). Approximating the Shapiro-Wilk W-test for non-normality. *Statistics and Computing*, 2(3), 117–119. [doi:10.1007/BF01891203](https://doi.org/10.1007/BF01891203)

Royston, P. (1993). A Toolkit for Testing for Non-Normality in Complete and Censored Samples. Journal of the Royal Statistical Society Series D (The Statistician), 42(1), 37–43. [doi:10.2307/2348109](https://doi.org/10.2307/2348109)

Royston, P. (1995). Remark AS R94: A Remark on Algorithm AS 181: The W-test for Normality. *Journal of the Royal Statistical Society Series C (Applied Statistics)*, 44(4), 547–551. [doi:10.2307/2986146](https://doi.org/10.2307/2986146). ```
