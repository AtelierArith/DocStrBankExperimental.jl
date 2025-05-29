```julia
findclosestbelow(needles, haystack)
```

インデックス可能なコレクション `haystack` の中で、各値 `needles` よりも小さい（すなわち「下」）最も近い値のインデックスを返します。そのような `haystack` の値が存在しない場合は、`firstindex(haystack)-1` を返します。

### 例

```julia
julia> findclosestbelow(3.5, 1:10)
3

julia> findclosestbelow(3:4, 1:10)
2-element Vector{Int64}:
 2
 3    
```
