```
Given(X₁, X₂ … Xₙ, Q) :: Query
```

これは、クエリのセットによって追加された名前付きパラメータで拡張されたコンテキストで `Q` を評価します。

```jldoctest
julia> unitknot[Given(:x => 2, It.x .+ 1)]
┼───┼
│ 3 │
```
