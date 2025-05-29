```
alm2cl(alm::Alm{Complex{T}}) where {T <: Number} -> Vector{T}
alm2cl(alm₁::Alm{Complex{T}}, alm₂::Alm{Complex{T}}) where {T <: Number} -> Vector{T}
```

1つまたは2つのフィールドの球面調和係数から $C_{\ell}$ を計算します。

# 引数

  * `alm₁::Alm{Complex{T}}`: 最初のフィールドの球面調和係数
  * `alm₂::Alm{Complex{T}}`: 2番目のフィールドの球面調和係数

# 戻り値

  * $$
    C_{\ell}
    $$

    を含む `Array{T}`。最初の要素は ℓ=0 を指します。
