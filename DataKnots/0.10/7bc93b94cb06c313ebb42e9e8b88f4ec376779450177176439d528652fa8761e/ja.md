```
Record(X₁, X₂ … Xₙ) :: Query
```

このクエリは、`X₁`, `X₂` … `Xₙ` によって生成されたフィールドを持つレコードを出力します。

```jldoctest
julia> unitknot[Lift(1:3) >> Record(It, It .* It)]
  │ #A  #B │
──┼────────┼
1 │  1   1 │
2 │  2   4 │
3 │  3   9 │
```

フィールドラベルはクエリから継承されます。

```jldoctest
julia> unitknot[Lift(1:3) >> Record(:x => It,
                                    :x² => It .* It)]
  │ x  x² │
──┼───────┼
1 │ 1   1 │
2 │ 2   4 │
3 │ 3   9 │
```
