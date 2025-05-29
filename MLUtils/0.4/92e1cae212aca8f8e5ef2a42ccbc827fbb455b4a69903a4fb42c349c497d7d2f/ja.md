```
unsqueeze(; dims)
```

配列に作用する関数を返し、`dims`で指定された位置にサイズ1の次元を挿入します。

# 例

```jldoctest
julia> rand(21, 22, 23) |> unsqueeze(dims=2) |> size
(21, 1, 22, 23)
```
