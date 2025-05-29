```
construct_from(args...; kwargs...)
```

コンテキストから型を推測できる場合、型を明示することなくオブジェクトを構築します。

# 例

```julia-repl
julia> vec::Vector{Vector{Int}} = construct_from(undef, 3);

julia> vec
3-element Vector{Vector{Int64}}:
 #undef
 #undef
 #undef
```
