```
MultiVector(::CliffordAlgebra, v::NTuple{N,T}) where {N,T<:Real}
MultiVector(::Type{<:CliffordAlgebra}, v::NTuple{N,T}) where {N,T<:Real}
```

提供されたベクトル v を 1-ベクトルに変換することで MultiVector を作成します。MultiVector の内部ストレージタイプは T です。
