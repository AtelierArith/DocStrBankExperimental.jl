```
random_mps(eltype::Type{<:Number}, sites::Vector{<:Index}; linkdims=1)
```

リンク次元 `linkdims` のタイプ `eltype` のランダム MPS を構築します。

`linkdims` は、非一様ボンド次元を持つ MPS を構築するために `length(linkdims) == length(sites) - 1` の `Vector{Int}` も受け入れることができます。
