```
Keep(X₁, X₂ … Xₙ) :: Query
```

`Keep` は名前付きクエリを評価し、その結果を後続の計算で利用できるようにします。

```jldoctest
julia> unitknot[Keep(:x => 2) >> It.x]
│ x │
┼───┼
│ 2 │
```

`Keep` はそれ以外に入力を変更しません。

```jldoctest
julia> unitknot[Lift(1) >> Keep(:x => 2) >> (It .+ It.x)]
┼───┼
│ 3 │
```
