```
joinlabels!(lmd, [lbls...]; delim = "_")
```

ラベル付きの多モーダルデータセットにおいて、`lbls`によって特定されたラベリング変数を、`delim`を文字列区切りとして使用する`join`によって、`String`型の単一のラベリング変数に統合します。

特に指定がない限り、この関数はすべてのラベルを結合します。

`lbls`は、ラベルのインデックスを示す`Integer`、またはラベリング変数の名前を示す`Symbol`であることができます。

# !!! 注意

# 結果のラベルは常に`String`型になります。

!!! 注意     結果のラベリング変数は常に基になる`DataFrame`の最後の列として追加されます。

# 例

```julia-repl
julia> lmd = LabeledMultiDataset(
           MultiDataset(
               [[2],[4]],
               DataFrame(
                   :id => [1, 2],
                   :age => [30, 9],
                   :name => ["Python", "Julia"],
                   :stat => [[sin(i) for i in 1:50000], [cos(i) for i in 1:50000]]
               )
           ),
           [1, 3],
       )
● LabeledMultiDataset
   ├─ labels
   │   ├─ id: Set([2, 1])
   │   └─ name: Set(["Julia", "Python"])
   └─ dimensionalities: (0, 1)
- モダリティ 1 / 2
   └─ 次元数: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    30
   2 │     9
- モダリティ 2 / 2
   └─ 次元数: 1
2×1 SubDataFrame
 Row │ stat
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…


julia> joinlabels!(lmd)
● LabeledMultiDataset
   ├─ labels
   │   └─ id_name: Set(["1_Python", "2_Julia"])
   └─ dimensionalities: (0, 1)
- モダリティ 1 / 2
   └─ 次元数: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    30
   2 │     9
- モダリティ 2 / 2
   └─ 次元数: 1
2×1 SubDataFrame
 Row │ stat
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…
```
