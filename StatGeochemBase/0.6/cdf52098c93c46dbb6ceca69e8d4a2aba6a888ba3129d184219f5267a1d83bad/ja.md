```julia
findclosestunequal(x::Collection, i::Integer)
```

`x[n] != x[i]` となる `i` に最も近いインデックス `n` を返します。`x` の不等値が見つからない場合は `i` を返します。

### 例

```julia
julia> x = [1, 2, 2, 3, 4]
5-element Vector{Int64}:
 1
 2
 2
 3
 4

julia> findclosestunequal(x, 2)
1

julia> findclosestunequal(x, 3)
4    
```
