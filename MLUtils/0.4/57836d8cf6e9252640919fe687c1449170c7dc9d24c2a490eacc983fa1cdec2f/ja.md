```
unbatch(x)
```

配列 `x` の最後の次元をアンスタックする、[`batch`](@ref) 操作の逆です。

他に [`unstack`](@ref) と [`chunk`](@ref) も参照してください。

# 例

```jldoctest
julia> unbatch([1 3 5 7;
                2 4 6 8])
4-element Vector{Vector{Int64}}:
 [1, 2]
 [3, 4]
 [5, 6]
 [7, 8]
```
