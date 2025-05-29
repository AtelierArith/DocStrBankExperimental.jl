```
ApproximateTwoSampleKSTest(x::AbstractVector{<:Real}, y::AbstractVector{<:Real})
```

`x` と `y` が同じ分布から抽出されたという帰無仮説に対して、異なる分布から抽出されたという対立仮説を検定する漸近的二標本コルモゴロフ–スミルノフ検定を実行します。

実装: [`pvalue`](@ref)

# 外部リンク

  * [片側検定の近似 (数学の百科事典)](https://www.encyclopediaofmath.org/index.php/Kolmogorov-Smirnov_test)

```
