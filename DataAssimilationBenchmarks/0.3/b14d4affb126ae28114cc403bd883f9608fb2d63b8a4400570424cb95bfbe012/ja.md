```
function CovM(type)
    Union{UniformScaling{T}, Diagonal{T, Vector{T}},
          Symmetric{T, Matrix{T}}} where T <: type
end
```

共分散行列型のユニオンの型コンストラクタであり、対称性や正定値演算子としての特性に基づく多重ディスパッチのためのものです。
