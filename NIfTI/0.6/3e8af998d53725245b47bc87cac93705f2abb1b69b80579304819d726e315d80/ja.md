```
function setaffine(h::NIfTIHeader, affine::Array{T,2}) where {T}
```

`NIfTIHeader`のアフィンを4x4アフィン行列`affine`に設定します。
