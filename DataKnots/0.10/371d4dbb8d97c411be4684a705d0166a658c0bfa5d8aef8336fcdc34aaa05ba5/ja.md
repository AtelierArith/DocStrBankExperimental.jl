```
Get(lbl::Symbol) :: Query
```

このクエリは、ラベルによってフィールド値を抽出します。

```jldoctest
julia> unitknot[Lift((x=1, y=2)) >> Get(:x)]
│ x │
┼───┼
│ 1 │
```

これは `It` を使用した短縮形があります。

```jldoctest
julia> unitknot[Lift((x=1, y=2)) >> It.x]
│ x │
┼───┼
│ 1 │
```

ラベルのないフィールドでは、序数ラベル (A, B, ...) を使用できます。

```jldoctest
julia> unitknot[Lift((1,2)) >> It.B]
┼───┼
│ 2 │
```
