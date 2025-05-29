```
getcells(t, n::Int)
```

Tiler または Table `t` のセル `n` を取得します。

各タプルが `(Point, Number)` であるタプルの配列を返します。

!!! note
    Luxor Tables と Tilers は、通常の Julia 列優先番号付けではなく、行から列の順に番号が付けられています：


```
 1  2  3  4  5
 6  7  8  9 10
11 12 13 14 15
16 17 18 19 20
```
