```
RawSparseTensor(indices::Union{PyObject,Array{T,2}}, value::Union{PyObject,Array{Float64,1}},
    m::Union{PyObject,Int64}, n::Union{PyObject,Int64}; is_diag::Bool=false) where T<:Integer
```

カスタム演算子を作成するための便利なラッパーです。ここで `indices` は0ベースです。
