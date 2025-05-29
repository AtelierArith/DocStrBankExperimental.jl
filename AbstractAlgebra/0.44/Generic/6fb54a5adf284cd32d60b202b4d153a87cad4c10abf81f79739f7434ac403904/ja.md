```
hooklength(Y::YoungTableau, i, j)
```

`Y`の`(i,j)`位置にある要素のフック長を返します。つまり、`(i,j)`-th ボックスの右側にある`i`-th 行のセルの数、`(i,j)`-th ボックスの下にある`j`-th 列のセルの数、そして`1`を足したものです。

`(i,j)`が表`Y`に存在しない場合は`0`を返します。

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

julia> hooklength(y, 1,1)
6

julia> hooklength(y, 1,3)
3

julia> hooklength(y, 2,4)
0
```
