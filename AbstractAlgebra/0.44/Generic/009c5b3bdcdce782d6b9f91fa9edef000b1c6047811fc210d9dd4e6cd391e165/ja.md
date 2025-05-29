```
getindex(Y::YoungTableau, n::Integer)
```

`size(Y)`-配列への列優先の線形インデックスを返します。ボックスが配列の外にある場合は`0`を返します。

# 例

```jldoctest
julia> y = YoungTableau([4,3,1])
┌───┬───┬───┬───┐
│ 1 │ 2 │ 3 │ 4 │
├───┼───┼───┼───┘
│ 5 │ 6 │ 7 │
├───┼───┴───┘
│ 8 │
└───┘

julia> y[1]
1

julia> y[2]
5

julia> y[4]
2

julia> y[6]
0
```
