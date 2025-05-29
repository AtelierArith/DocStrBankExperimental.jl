```
Filter(X) :: Query
```

このクエリは、与えられた条件を満たす入力の要素を出力します。

```jldoctest
julia> unitknot[Lift(1:5) >> Filter(isodd.(It))]
──┼───┼
1 │ 1 │
2 │ 3 │
3 │ 5 │
```

述語クエリが空の出力を生成する場合、条件は失敗したと見なされます。

```jldoctest
julia> unitknot[Lift('a':'c') >> Filter(missing)]
(empty)
```

述語が複数の出力を生成する場合、少なくとも1つの出力値が`true`であれば、条件は成功します。

```jldoctest
julia> unitknot[Lift('a':'c') >> Filter([true,false])]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```
