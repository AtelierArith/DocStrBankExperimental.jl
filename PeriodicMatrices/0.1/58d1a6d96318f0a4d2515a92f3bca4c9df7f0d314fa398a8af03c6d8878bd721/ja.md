```
pgschur!(A::Array{Float64,3}, S::Union{Vector{Bool},BitVector}; kwargs...)
```

`pgschur`と同様ですが、入力行列`A`をワークスペースとして使用します。
