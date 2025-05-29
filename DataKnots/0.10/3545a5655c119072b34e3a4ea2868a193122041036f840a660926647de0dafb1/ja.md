```
Join(X) :: Query
```

`Join(X)`は、ソースコンテキスト内で`X`を評価し、それを入力レコードのフィールドとして追加します。

```jldoctest
julia> unitknot[Record(:x => 1) >> Each(Record(:y => 2 .* It.x) >> Join(It.x))]
│ y  x │
┼──────┼
│ 2  1 │
```
