```
Lift(val) :: Query
```

これは任意の値を定数クエリに変換します。

```jldoctest
julia> unitknot[Lift("Hello")]
┼───────┼
│ Hello │
```

`AbstractVector` オブジェクトは複数のクエリになります。

```jldoctest
julia> unitknot[Lift('a':'c')]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```

ベクトルのカーディナリティを指定するには、`:x0to1`、`:x0toN`、`:x1to1`、または `:x1toN` を追加します。

```jldoctest
julia> unitknot[Lift('a':'c', :x1toN)]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```

`missing` 値は出力のないクエリを作成します。

```jldoctest
julia> unitknot[Lift(missing)]
(empty)
```
