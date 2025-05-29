```
rowlength(Y::YoungTableau, i, j)
```

`Y`の`(i,j)`のボックスでの行の長さを返します。すなわち、`Y`の図の`i`-行目のボックスの中で`(i,j)`-ボックスの右側にあるボックスの数です。

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

julia> Generic.rowlength(y, 1,2)
2

julia> Generic.rowlength(y, 2,3)
0

julia> Generic.rowlength(y, 3,3)
0
```
