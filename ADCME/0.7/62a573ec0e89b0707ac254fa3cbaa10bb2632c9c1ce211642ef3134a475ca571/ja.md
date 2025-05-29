```
dense(inputs::Union{PyObject, Array{<:Real}}, units::Int64, args...; 
    activation::Union{String, Function} = nothing, kwargs...)
```

指定された活性化関数 `activation` を持つ完全接続層を作成します。
