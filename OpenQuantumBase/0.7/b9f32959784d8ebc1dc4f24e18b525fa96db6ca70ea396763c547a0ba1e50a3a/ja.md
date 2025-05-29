```
function ConstantCouplings(mats::Union{Vector{Matrix{T}},Vector{SparseMatrixCSC{T,Int}}}; unit=:h) where {T<:Number}
```

`ConstantCouplings`オブジェクトのコンストラクタ。`mats`は行列の1次元配列です。`str_rep`は結合項のオプションの文字列表現です。`unit`は単位で、`:h`または`:ħ`です。`mats`は単位が`:h`の場合、$2π$でスケーリングされます。
