```
anafast(map::HealpixMap{Float64, RingOrder, AA}; lmax=nothing, mmax=nothing, niter::Integer = 3) where {T <: Real,AA <: AbstractArray{T,1}} -> Vector{Float64}
anafast(map₁::HealpixMap{Float64, RingOrder, AA}, map₂::HealpixMap{Float64, RingOrder, AA}; lmax=nothing, mmax=nothing, niter::Integer = 3) where {T <: Real,AA <: AbstractArray{T,1}} -> Vector{Float64}
```

ヒールピックスマップのパワースペクトルを計算します。`map2`が指定されている場合は、2つのマップ間のクロススペクトルを計算します。モノポールやダイポールの除去は行われません。入力マップはリング順序である必要があります。

# 引数:

  * `map₁::HealpixMap{Float64, RingOrder, AA}`: 最初のフィールドの球面調和係数
  * `map₂::HealpixMap{Float64, RingOrder, AA}`: 2番目のフィールドの球面調和係数

# 戻り値:

  * $$
    C_{\ell}
    $$

    を含む`Array{T}`で、最初の要素はℓ=0を指します。
