```
insertmodality!(md, col, new_modality, existing_variables)
insertmodality!(md, new_modality, existing_variables)
```

`new_modality`を新しいモダリティとしてマルチモーダルデータセットに挿入し、データセットを返します。既存の変数は、対応するインデックスを`existing_variables`として渡すことで、新しいモダリティに追加できます。`col`が指定されている場合、変数はインデックス`col`から挿入されます。

# 引数

  * `md`は`MultiDataset`です。
  * `col`は、`new_modality`の列を挿入する列を示す`Integer`です。
  * `new_modality`は、マルチモーダルデータセットに新しいモダリティのサブデータフレームとして追加される`AbstractDataFrame`です。
  * `existing_variables`は`AbstractVector{Integer}`または`AbstractVector{Symbol}`です。これは、新しいモダリティに挿入するマルチモーダルデータセットの内部データフレーム構造の変数を示します。

# 例

```julia-repl
julia> df = DataFrame(
           :name => ["Python", "Julia"],
           :stat1 => [[sin(i) for i in 1:50000], [cos(i) for i in 1:50000]]
       )
2×2 DataFrame
 Row │ name    stat1
     │ String  Array…
─────┼───────────────────────────────────────────
   1 │ Python  [0.841471, 0.909297, 0.14112, -0…
   2 │ Julia   [0.540302, -0.416147, -0.989992,…

julia> md = MultiDataset(df; group = :all)
● MultiDataset
   └─ dimensionalities: (0, 1)
- Modality 1 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Modality 2 / 2
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…

julia> insertmodality!(md, DataFrame(:age => [30, 9]))
● MultiDataset
   └─ dimensionalities: (0, 1, 0)
- Modality 1 / 3
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Modality 2 / 3
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…
- Modality 3 / 3
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    30
   2 │     9

julia> md.data
2×3 DataFrame
 Row │ name    stat1                              age
     │ String  Array…                             Int64
─────┼──────────────────────────────────────────────────
   1 │ Python  [0.841471, 0.909297, 0.14112, -0…     30
   2 │ Julia   [0.540302, -0.416147, -0.989992,…      9
```

または、列を選択する場合

```julia-repl
julia> df = DataFrame(
           :name => ["Python", "Julia"],
           :stat1 => [[sin(i) for i in 1:50000], [cos(i) for i in 1:50000]]
       )
2×2 DataFrame
 Row │ name    stat1
     │ String  Array…
─────┼───────────────────────────────────────────
   1 │ Python  [0.841471, 0.909297, 0.14112, -0…
   2 │ Julia   [0.540302, -0.416147, -0.989992,…

julia> md = MultiDataset(df; group = :all)
● MultiDataset
   └─ dimensionalities: (0, 1)
- Modality 1 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Modality 2 / 2
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…

julia> insertmodality!(md, 2, DataFrame(:age => [30, 9]))
● MultiDataset
   └─ dimensionalities: (1, 0)
- Modality 1 / 2
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
    1 │ [0.841471, 0.909297, 0.14112, -0…
    2 │ [0.540302, -0.416147, -0.989992,…
- Modality 2 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    30
   2 │     9
- スペア変数
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia

julia> md.data
2×3 DataFrame
 Row │ name    age    stat1
     │ String  Int64  Array…
─────┼──────────────────────────────────────────────────
   1 │ Python     30  [0.841471, 0.909297, 0.14112, -0…
   2 │ Julia       9  [0.540302, -0.416147, -0.989992,…
```

または、既存の変数を追加する場合：

```julia-repl
julia> df = DataFrame(
           :name => ["Python", "Julia"],
           :stat1 => [[sin(i) for i in 1:50000], [cos(i) for i in 1:50000]]
       )
2×2 DataFrame
 Row │ name    stat1
     │ String  Array…
─────┼───────────────────────────────────────────
   1 │ Python  [0.841471, 0.909297, 0.14112, -0…
   2 │ Julia   [0.540302, -0.416147, -0.989992,…

julia> md = MultiDataset([[2]], df)
● MultiDataset
   └─ dimensionalities: (1,)
- Modality 1 / 1
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…
- スペア変数
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia


julia> insertmodality!(md, DataFrame(:age => [30, 9]); existing_variables = [1])
● MultiDataset
   └─ dimensionalities: (1, 0)
- Modality 1 / 2
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat1
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…
- Modality 2 / 2
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ age    name
     │ Int64  String
─────┼───────────────
   1 │    30  Python
   2 │     9  Julia
```
