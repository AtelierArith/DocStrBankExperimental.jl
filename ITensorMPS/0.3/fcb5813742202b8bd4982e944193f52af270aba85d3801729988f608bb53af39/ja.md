```
random_mps(sites::Vector{<:Index}; linkdims=1)
random_mps(eltype::Type{<:Number}, sites::Vector{<:Index}; linkdims=1)
```

リンク次元 `linkdims` を持つランダムな MPS を構築します。デフォルトでは要素タイプは `Float64` です。

`linkdims` はまた、非一様なボンド次元を持つ MPS を構築するために `length(linkdims) == length(sites) - 1` の `Vector{Int}` を受け入れることができます。
