```
synalm!([rng=GLOBAL_RNG], Cl::AbstractArray{T,3}, alms) where T
```

球面調和係数のインプレース合成、スペクトルが与えられた場合。

# 引数:

  * `Cl::AbstractArray{T,3}`: comp, comp, ℓ の次元を持つ配列
  * `alms::Union{NTuple{N,Alm}, Vector{Alm}}`: 埋めるためのAlmの配列

# 例

```julia
nside = 16
C0 = [3.  2.;  2.  5.]
Cl = repeat(C0, 1, 1, 3nside)  # ℓで一定のスペクトル
alms = [Alm{Complex{Float64}}(3nside-1, 3nside-1) for i in 1:2]
synalm!(Cl, alms)
```
