```
strainvtot!(::Type{DeforModelRed2DStrain}, t::Matrix{T}, v::Vector{T}) where {T}
```

3次元ひずみベクトルを2x2ひずみ成分の行列（対称テンソル）に変換します。
