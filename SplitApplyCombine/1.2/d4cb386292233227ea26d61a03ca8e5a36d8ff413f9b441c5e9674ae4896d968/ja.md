```
filterview(f, a)
```

配列 `a` の要素のうち、`f` が `false` でないもののビューを返します。`filter(f, a)` に似ていますが、コピーの代わりにビューを返します。フィルタリングされたインデックスは一度計算され、配列が変更されても更新されません。

# 例

```
julia> a = [1, 2, 3];

julia> b = filterview(isodd, a)
2-element view(::Vector{Int64}, [1, 3]) with eltype Int64:
 1
 3

julia> b[2] = 10;

julia> a
3-element Vector{Int64}:
  1
  2
 10

julia> b
2-element view(::Vector{Int64}, [1, 3]) with eltype Int64:
  1
 10
```
