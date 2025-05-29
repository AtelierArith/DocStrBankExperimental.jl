```
gumbelfitpwm(...)
```

確率加重モーメントを用いてGumbelパラメータを推定します。

# 実装

[Landwehr *et al. (1979)](https://agupubs.onlinelibrary.wiley.com/doi/abs/10.1029/WR015i005p01055) によって説明されている確率加重モーメントによる推定は、定常状態の場合にのみ可能です。

他の方法については、[`gumbelfitpwm`](@ref)、[`gevfit`](@ref)、[`gevfitbayes`](@ref)、および[`BlockMaxima`](@ref)を参照してください。

# 参考文献

Landwehr, J. M., Matalas, N. C. and Wallis, J. R. (1979). 確率加重モーメントは、Gumbelパラメータと分位数を推定するいくつかの従来の技術と比較されます。 *Water Resources Research*, 15:1055–1064.
