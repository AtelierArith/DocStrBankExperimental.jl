```
removemodality!(md, indices)
removemodality!(md, index)
```

`i`-番目のモダリティをマルチモーダルデータセットから削除し、データセットを返します。

注意: モダリティとその中のすべての変数を完全に削除するには、代わりに [`dropmodalities!`](@ref) を使用してください。

# 引数

  * `md` は `MultiDataset` です;
  * `index` はマルチモーダルデータセットから削除するモダリティを示す `Integer` です;
  * `indices` はマルチモーダルデータセットから削除するモダリティを示す `AbstractVector{Integer}` です;

# 例

```julia-repl
julia> df = DataFrame(:name => ["Python", "Julia"],
                      :age => [25, 26],
                      :sex => ['M', 'F'],
                      :height => [180, 175],
                      :weight => [80, 60])
                     )
2×5 DataFrame
 Row │ name    age    sex   height  weight
     │ String  Int64  Char  Int64   Int64
─────┼─────────────────────────────────────
   1 │ Python     25  M        180      80
   2 │ Julia      26  F        175      60

julia> md = MultiDataset([[1, 2],[3],[4],[5]], df)
● MultiDataset
   └─ dimensionalities: (0, 0, 0, 0)
- Modality 1 / 4
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ name    age
     │ String  Int64
─────┼───────────────
   1 │ Python     25
   2 │ Julia      26
- Modality 2 / 4
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F
- Modality 3 / 4
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ height
     │ Int64
─────┼────────
   1 │    180
   2 │    175
- Modality 4 / 4
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ weight
     │ Int64
─────┼────────
   1 │     80
   2 │     60

julia> removemodality!(md, [3])
● MultiDataset
   └─ dimensionalities: (0, 0, 0)
- Modality 1 / 3
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ name    age
     │ String  Int64
─────┼───────────────
   1 │ Python     25
   2 │ Julia      26
- Modality 2 / 3
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F
- Modality 3 / 3
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ weight
     │ Int64
─────┼────────
   1 │     80
   2 │     60
- Spare variables
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ height
     │ Int64
─────┼────────
   1 │    180
   2 │    175

julia> removemodality!(md, [1,2])
● MultiDataset
   └─ dimensionalities: (0,)
- Modality 1 / 1
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ weight
     │ Int64
─────┼────────
   1 │     80
   2 │     60
- Spare variables
   └─ dimensionality: 0
2×4 SubDataFrame
 Row │ name    age    sex   height
     │ String  Int64  Char  Int64
─────┼─────────────────────────────
   1 │ Python     25  M        180
   2 │ Julia      26  F        175

```
