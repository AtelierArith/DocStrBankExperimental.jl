```
synfast!(cl::Vector{T}, map::HealpixMap{T, RingOrder}, lmax::Integer, rng::AbstractRNG) where {T <: Real}
synfast!(cl::Vector{T}, map::HealpixMap{T, RingOrder}, lmax::Integer) where {T <: Real}
synfast!(cl::Vector{T}, map::HealpixMap{T, RingOrder}, rng::AbstractRNG) where {T <: Real}
synfast!(cl::Vector{T}, map::HealpixMap{T, RingOrder}) where {T <: Real}
```

与えられたパワースペクトル $C_{\ell}$ からマップを生成します。結果は入力として渡された `HealpixMap` に保存されます。

# 引数:

  * `cl::AbstractVector{T}`: パワースペクトル成分 $C_{\ell}$ を表す配列。
  * `map::HealpixMap{T, RingOrder}`: 結果を含むマップ。
  * `lmax::Integer`: 最大 $ℓ$ 係数。指定されていない場合は `length(cl)-1` にデフォルト設定されます。
  * `rng::AbstractRNG` : （オプション）$a_{\ell m}$ を生成するために使用されるRNG。プロセスの再現性を保証するために事前にシードを設定することができます。
