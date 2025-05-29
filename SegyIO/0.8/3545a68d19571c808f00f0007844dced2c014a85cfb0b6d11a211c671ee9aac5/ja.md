```
使用法: find_next_delim(x::AbstractVector, i::Int, probe_length::Int)
```

開始インデックス `i` から、異なる値を持つベクトル内の次の要素のインデックスを返します。

# 例

```
julia> x = vec([1 1 1 2 2 2 2 3 3 3 3]);

julia> find_next_delim(x, 1, 1)
4

julia> find_next_delim(x, 4, 1)
8
```
