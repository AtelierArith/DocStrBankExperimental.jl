```julia
pois_rand(λ)
pois_rand(rng::AbstractRNG, λ)
```

ポアソン(λ)分布の乱数を高速ポリアルゴリズムを使用して生成します。

## 例

```julia
# シンプルなポアソン乱数
pois_rand(λ)

# 別のRNGを使用
using RandomNumbers
rng = Xorshifts.Xoroshiro128Plus()
pois_rand(rng,λ)
```
