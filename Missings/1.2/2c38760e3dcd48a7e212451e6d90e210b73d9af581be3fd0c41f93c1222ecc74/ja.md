```
emptymissing(f)
```

少なくとも1つの位置引数 `x` を受け取り、`x` が空である場合（`isempty(x)` が `true` を返す）には `missing` を返し、そうでない場合には `f(x, args...; kwargs...)` を返す関数を返します。ここで、`args` は `f` に渡される位置引数であり、`kwargs` はそのキーワード引数です。

# 例

```
julia> emptymissing(last)([])
missing

julia> emptymissing(last)([1, 2, 3])
3

julia> emptymissing(first)([], 2)
missing

julia> emptymissing(first)([1], 2)
1-element Vector{Int64}:
1
```
