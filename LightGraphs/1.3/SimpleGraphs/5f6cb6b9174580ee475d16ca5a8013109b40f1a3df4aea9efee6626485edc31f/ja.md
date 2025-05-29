```
binary_tree(k::Integer)
```

深さ `k` の [二分木](https://en.wikipedia.org/wiki/Binary_tree) を作成します。

# 例

```jldoctest
julia> binary_tree(4)
{15, 14} 無向単純 Int64 グラフ

julia> binary_tree(Int8(5))
{31, 30} 無向単純 Int8 グラフ
```
