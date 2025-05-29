```julia
findmatches(needles, haystack)
```

`haystack`内の各`needles`の値に等しい最初の値の線形インデックスを返します（存在する場合）。存在しない場合は0を返します。

### 例

```julia
julia> findmatches([3,5],1:10)
2-element Vector{Int64}:
 3
 5
```
