```
synalm(cl::Vector{T}, lmax::Integer, mmax::Integer, rng::AbstractRNG) where {T <: Real}
synalm(cl::Vector{T}, lmax::Integer, mmax::Integer) where {T <: Real}
synalm(cl::Vector{T}, lmax::Integer, rng::AbstractRNG) where {T <: Real}
synalm(cl::Vector{T}, lmax::Integer) where {T <: Real}
synalm(cl::Vector{T}, rng::AbstractRNG) where {T <: Real}
synalm(cl::Vector{T}) where {T <: Real}
```

与えられたパワースペクトル $C_{\ell}$ から $a_{\ell m}$ のセットを生成します。出力は指定された lmax の新しい `Alm` オブジェクトに書き込まれます。

# 引数:

  * `cl::AbstractVector{T}`: パワースペクトル成分 $C_{\ell}$ を表す配列で、$\ell = 0$ から始まります。
  * `lmax::Integer`: 最大 $ℓ$ コエフィシエントで、指定されていない場合は `length(cl)-1` にデフォルト設定されます。
  * `mmax::Integer`: 最大 $m$ コエフィシエントで、指定されていない場合は `lmax` にデフォルト設定されます。
  * `rng::AbstractRNG` : （オプション）$a_{\ell m}$ を生成するために使用される RNG です。これにより、プロセスの再現性を保証するために事前にシードを設定できます。
