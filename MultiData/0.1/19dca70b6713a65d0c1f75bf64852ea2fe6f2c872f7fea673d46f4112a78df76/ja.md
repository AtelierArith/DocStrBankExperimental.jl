```
LabeledMultiDataset(md, labeling_variables)
```

`AbstractMultiDataset`にいくつかのラベリング変数を関連付けることによって`LabeledMultiDataset`を作成します。ラベリング変数は、列インデックス（`Int`）または列インデックスのベクター（`Vector{Int}`）として指定されます。

# 引数

  * `md` は元の `AbstractMultiDataset` です;
  * `labeling_variables` は、ラベルとして設定される変数のインデックスを示す整数の `AbstractVector` です。

# 例

```julia-repl
julia> lmd = LabeledMultiDataset(MultiDataset([[2],[4]], DataFrame(
           :id => [1, 2],
           :age => [30, 9],
           :name => ["Python", "Julia"],
           :stat => [[sin(i) for i in 1:50000], [cos(i) for i in 1:50000]]
       )), [1, 3])
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

```
