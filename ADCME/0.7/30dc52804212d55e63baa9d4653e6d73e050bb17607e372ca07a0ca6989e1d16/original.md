```
RawSparseTensor(indices::Union{PyObject,Array{T,2}}, value::Union{PyObject,Array{Float64,1}},
    m::Union{PyObject,Int64}, n::Union{PyObject,Int64}; is_diag::Bool=false) where T<:Integer
```

A convenient wrapper for making custom operators. Here `indices` is 0-based. 
