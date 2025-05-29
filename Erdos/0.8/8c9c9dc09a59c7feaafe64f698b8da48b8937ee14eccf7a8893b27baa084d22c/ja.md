```
attracting_components(g)
```

有向グラフ `g` の引き寄せ成分のリストを表す整数のベクトルのベクトルを返します。

引き寄せ成分は、出て行くエッジを持たない強連結成分のサブセットです。

# 例

```jldoctest
julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0])
{5, 6} 有向単純 Int64 グラフ

julia> strongly_connected_components(g)
2-element Array{Array{Int64,1},1}:
 [4, 5]
 [1, 2, 3]

julia> attracting_components(g)
1-element Array{Array{Int64,1},1}:
 [4, 5]
```
