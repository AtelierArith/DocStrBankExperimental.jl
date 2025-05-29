```
UnequalVarianceTTest(x::AbstractVector{T<:Real}, y::AbstractVector{T<:Real})
```

`x` と `y` が平均が等しい分布から来ているという帰無仮説に対して、分布が異なる平均を持つという対立仮説のもとで、不等分散の二標本t検定を実行します。

この検定はウェルチのt検定として知られることがあります。等分散t検定とは異なり、ウェルチ・サッタースウェイトの方程式を使用して検定の自由度を計算します：

$$
    ν_{χ'} ≈ \frac{\left(\sum_{i=1}^n k_i s_i^2\right)^2}{\sum_{i=1}^n
        \frac{(k_i s_i^2)^2}{ν_i}}
$$

実装：[`pvalue`](@ref), [`confint`](@ref)
