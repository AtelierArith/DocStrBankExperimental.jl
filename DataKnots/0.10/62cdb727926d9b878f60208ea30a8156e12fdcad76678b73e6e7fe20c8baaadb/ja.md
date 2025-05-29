```
Collect(X₁, X₂ … Xₙ) :: Query
```

組み合わせ形式では、`Collect(X₁, X₂ … Xₙ)`は入力レコードにフィールド`X₁`、`X₂` … `Xₙ`を追加します。

```jldoctest
julia> unitknot[Record(:x => 1) >> Collect(:y => 2 .* It.x)]
│ x  y │
┼──────┼
│ 1  2 │
```

フィールドがすでに存在する場合は、置き換えられます。

```jldoctest
julia> unitknot[Record(:x => 1) >> Collect(:x => 2 .* It.x)]
│ x │
┼───┼
│ 2 │
```

フィールドを削除するには、その値を`nothing`に設定します。

```jldoctest
julia> unitknot[Record(:x => 1) >> Collect(:y => 2 .* It.x, :x => nothing)]
│ y │
┼───┼
│ 2 │
```

---

```
Each(X >> Record) :: Query
```

クエリ形式では、`Collect`はソースレコードにフィールドを追加します。

```jldoctest
julia> unitknot[Lift(1) >> Label(:x) >> Collect]
│ x │
┼───┼
│ 1 │
```
