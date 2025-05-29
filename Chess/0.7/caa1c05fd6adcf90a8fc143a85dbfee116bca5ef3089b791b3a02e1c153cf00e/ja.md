```
squaresbetween(s1::Square, s2::Square)
```

`s1` と `s2` の間の直線、ファイル、または対角線上の正方形の集合。

`SQ_A4` にいるクイーンが空のボード上で `s2` を攻撃する場合、この関数は `s1` のクイーンが `s2` を攻撃するのをブロックする駒が置かれる正方形の集合を返します。

# 例

```julia-repl
julia> squaresbetween(SQ_A4, SQ_D4) == SquareSet(SQ_B4, SQ_C4)
true

julia> squaresbetween(SQ_F7, SQ_A2)
SquareSet:
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  #  -  -  -
 -  -  -  #  -  -  -  -
 -  -  #  -  -  -  -  -
 -  #  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
```
