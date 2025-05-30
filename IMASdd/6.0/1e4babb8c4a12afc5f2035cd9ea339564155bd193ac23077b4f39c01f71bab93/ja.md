```
resize!(@nospecialize(ids::IDSvector{T}), time0::Float64; wipe::Bool=true) where {T<:IDSvectorTimeElement}
```

時間に基づいて依存する配列のサイズを変更します。
