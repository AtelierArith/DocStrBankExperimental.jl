```
BlockArray{T}(::UndefInitializer, block_sizes::Vararg{AbstractVector{<:Integer}, N}) where {T, N}
```

`Array{T,N}`型のブロックを持つ`N`次元の`BlockArray`を、`block_sizes`で定義されたサイズで構築します。ブロックは`similar`を使用して割り当てられ、したがって各ブロック内の要素は初期化されていません。

# 例

```jldoctest
julia> B = BlockArray{Int8}(undef, [1,2]);

julia> B[Block(1)] .= 2;

julia> B[Block(2)] .= 3;

julia> B
2-blocked 3-element BlockVector{Int8}:
 2
 ─
 3
 3
```
