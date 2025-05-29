```
almxfl!(alm::Alm{Complex{T}}, fl::AA) where {T <: Number,AA <: AbstractArray{T,1}}
```

a*ℓmをベクトルb*ℓでインプレースで乗算し、ℓ依存関数を表します。

# 引数

  * `alms::Alm{Complex{T}}`: 球面調和関数の係数を含む`Alm`オブジェクト
  * `fl::AbstractVector{T}`: a*ℓmに乗算される要素f*ℓを含む配列
