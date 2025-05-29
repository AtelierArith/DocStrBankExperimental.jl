```julia
findclosest(needles, haystack)
```

インデックス可能なコレクション `haystack` の中で、各値 `needles` に対して数値的に最も近い値のインデックスを返します。複数の値が同じくらい近い場合は、最初のものが使用されます。

### 例

```julia
julia> findclosest(3.4, 1:10)
3

julia> findclosest(3:4, 1:10)
2-element Vector{Int64}:
 3
 4
```
