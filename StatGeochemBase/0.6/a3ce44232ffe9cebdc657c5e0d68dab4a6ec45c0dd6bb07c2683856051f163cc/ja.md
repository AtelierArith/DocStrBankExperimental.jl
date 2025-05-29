```julia
findclosestabove(needles, haystack)
```

インデックス可能なコレクション `haystack` の中で、`needles` の各値よりも大きい（すなわち「上」）最も近い値のインデックスを返します。そのような値が存在しない場合は、`lastindex(haystack)+1` を返します。

### 例

```julia
julia> findclosestabove(3.5, 1:10)
4

julia> findclosestabove(3:4, 1:10)
2-element Vector{Int64}:
 4
 5
```
