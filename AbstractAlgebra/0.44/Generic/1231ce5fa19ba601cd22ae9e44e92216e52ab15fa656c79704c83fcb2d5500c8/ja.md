```
collength(Y::YoungTableau, i, j)
```

`Y`のボックス`(i,j)`における列の長さを返します。すなわち、`Y`の図の`j`-列において、`(i,j)`-ボックスの下にあるボックスの数です。

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

julia> Generic.collength(y, 1,1)
2

julia> Generic.collength(y, 1,3)
1

julia> Generic.collength(y, 2,4)
0
```
