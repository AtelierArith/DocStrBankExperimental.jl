```
almxfl(alm::Alm{Complex{T}}, fl::AbstractVector{T}) where {T <: Number} -> Alm{T}
```

a*ℓmとℓ依存関数を表すベクトルb*ℓを掛け算しますが、入力として渡されたa_ℓmは変更しません。

# 引数

  * `alms::Alm{Complex{T}}`: 球面調和関数の係数を含む`Alm`オブジェクト
  * `fl::AbstractVector{T}`: a*ℓmに掛け算される要素f*ℓを含む配列

# 戻り値

  * `Alm{Complex{T}}`: a*ℓm * f*ℓの結果。
