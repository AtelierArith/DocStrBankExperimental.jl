```
gpfitpwm(...)
```

確率加重モーメントを用いてGPパラメータを推定します。

# 実装

[Hosking and Wallis (1987)](https://www.jstor.org/stable/1269343?seq=1) に記載されている確率加重モーメントによる推定は、定常状態の場合にのみ可能です。

他の方法については、[`gpfitpwm`](@ref)、[`gpfit`](@ref)、[`gpfitbayes`](@ref)、および[`ThresholdExceedance`](@ref)を参照してください。

# 参考文献

Hosking, J. R. M. and Wallis, J. R. (1987). Generalized Pareto分布のパラメータと分位数の推定, *Technometrics*, 29:339-349.
