```
synfast(cl::Vector{T}, nside::Integer, lmax::Integer, rng::AbstractRNG) where {T <: Real}
synfast(cl::Vector{T}, nside::Integer, lmax::Integer) where {T <: Real}
synfast(cl::Vector{T}, nside::Integer, rng::AbstractRNG) where {T <: Real}
synfast(cl::Vector{T}, nside::Integer) where {T <: Real}
```

与えられたNsideから、与えられたパワースペクトル$C_{\ell}$を用いて`HealpixMap`を生成します。

# 引数:

  * `cl::AbstractVector{T}`: パワースペクトル成分$C_{\ell}$を表す配列。
  * `nside::Integer`: 結果を含むマップのnside。
  * `lmax::Integer`: 最大$ℓ$係数。指定されていない場合は`length(cl)`-1がデフォルトとなります。
  * `rng::AbstractRNG` : （オプション）$a_{\ell m}$を生成するために使用されるRNG。これにより、プロセスの再現性を保証するために事前にシードを設定できます。
