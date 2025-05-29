```
gevfitpwm(...)
```

確率加重モーメントを用いてGEVパラメータを推定します。

# 実装

確率加重モーメントを用いた推定は、[Hosking *et al*. (1985)](https://www.tandfonline.com/doi/abs/10.1080/00401706.1985.10488049)で説明されているように、定常状態の場合にのみ可能です。

他の手法については、[`gevfitpwm`](@ref)、[`gevfit`](@ref)、[`gevfitbayes`](@ref)、および[`BlockMaxima`](@ref)を参照してください。

# 参考文献

Hosking, J. R. M., Wallis, J. R. and Wood, E. F. (1985). 確率加重モーメント法による一般化極値分布の推定。 *Technometrics*, 27:251-261.
