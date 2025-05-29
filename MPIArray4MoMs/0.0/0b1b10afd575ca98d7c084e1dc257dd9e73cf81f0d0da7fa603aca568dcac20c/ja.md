```
ArrayChunk{T, N} <:AbstractArray{T, N}
```

カスタムインデックスを持つ配列チャンク。

```
data::Array{T, N}
indices::NTuple{N, Union{UnitRange{Int}, Vector{Int}}}
```
