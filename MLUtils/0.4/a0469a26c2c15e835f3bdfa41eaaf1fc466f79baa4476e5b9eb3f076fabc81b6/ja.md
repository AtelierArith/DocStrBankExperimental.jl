```
group_counts(x)
```

`x`の各要素が出現する回数をカウントします。

関連情報は[`group_indices`](@ref)を参照してください。

# 例

```jldoctest
julia> group_counts(['a', 'b', 'b'])
Dict{Char, Int64} with 2 entries:
  'a' => 1
  'b' => 2
```
