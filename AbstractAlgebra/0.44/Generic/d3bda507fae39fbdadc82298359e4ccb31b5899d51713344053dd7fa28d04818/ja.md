```
conj(Y::YoungTableau)
```

共役テーブルを返します。すなわち、主対角線を通して反射されたテーブルです。

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

julia> conj(y)
┌───┬───┬───┐
│ 1 │ 5 │ 8 │
├───┼───┼───┘
│ 2 │ 6 │
├───┼───┤
│ 3 │ 7 │
├───┼───┘
│ 4 │
└───┘
```
