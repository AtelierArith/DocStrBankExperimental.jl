```
synalm([rng=GLOBAL_RNG], Cl::AbstractArray{T,3}, nside::Int) where T
```

# 引数:

  * `Cl::AbstractArray{T,3}`: comp, comp, ℓ の次元を持つ配列
  * `nside::Int`: healpix 解像度

# 戻り値:

  * `Vector{Alm{T}}`: 各コンポーネントの球面調和関数の実現

# 例

```julia
nside = 16
C0 = [3.  2.;  2.  5.]
Cl = repeat(C0, 1, 1, 3nside)  # ℓ に対して定数のスペクトル
alms = synalm(Cl, nside)
```
