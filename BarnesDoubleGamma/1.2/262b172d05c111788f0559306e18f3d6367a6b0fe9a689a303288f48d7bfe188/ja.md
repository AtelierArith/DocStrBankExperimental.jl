```
log_barnesdoublegamma(z, τ)
```

バーンズG関数の対数 $\log(G(z; τ))$。高精度の場合、非常に高価になる可能性があります。

# 例

```jldoctest
julia> z = 1; τ = sqrt(3); log_barnesdoublegamma(z, τ)
-3.5564013784958066e-9

julia> z = sqrt(big"2"); τ = sqrt(big"3"); log_barnesdoublegamma(z, τ)
0.293394920968626643183216869255154162603276275448888004730390602371621786480874
```
