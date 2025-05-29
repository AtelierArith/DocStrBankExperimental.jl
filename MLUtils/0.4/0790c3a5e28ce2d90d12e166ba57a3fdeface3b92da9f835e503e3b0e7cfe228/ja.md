```
unstack(xs; dims)
```

与えられた `xs` を指定された次元 `dims` に沿って配列の配列に展開します。

これは [stack](https://docs.julialang.org/en/v1/base/arrays/#Base.stack) の逆操作です。

他に [`unbatch`](@ref) と [`chunk`](@ref) も参照してください。

# 例

```jldoctest
julia> unstack([1 3 5 7; 2 4 6 8], dims=2)
4-element Vector{Vector{Int64}}:
 [1, 2]
 [3, 4]
 [5, 6]
 [7, 8]
```
