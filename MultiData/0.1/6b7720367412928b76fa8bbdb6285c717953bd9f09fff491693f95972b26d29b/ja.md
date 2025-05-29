```
dropmodalities!(md, indices)
dropmodalities!(md, index)
```

`i`-番目のモダリティをマルチモーダルデータセットから削除し、その中のすべての変数を削除して、データセット自体を返します。

注意: 削除された変数が他のモダリティに含まれている場合、それらも削除されます。これにより、`i`-番目以外の追加のモダリティが削除される可能性があります。

変数を削除せずにモダリティを削除する意図がある場合は、代わりに [`removemodality!`](@ref) を使用してください。

# 引数

  * `md` は `MultiDataset` です;
  * `index` は削除するモダリティのインデックスを示す `Integer` です;
  * `indices` は削除するモダリティのインデックスを示す `AbstractVector{Integer}` です。

# 例

```julia-repl
julia> df = DataFrame(:name => ["Python", "Julia"], :age => [25, 26], :sex => ['M', 'F'], :height => [180, 175], :weight => [80, 60])
2×5 DataFrame
 Row │ name    age    sex   height  weight
     │ String  Int64  Char  Int64   Int64
─────┼─────────────────────────────────────
   1 │ Python     25  M        180      80
   2 │ Julia      26  F        175      60

julia> md = MultiDataset([[1, 2],[3,4],[5],[2,3]], df)
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
2×2 SubDataFrame
 Row │ sex   height
     │ Char  Int64
─────┼──────────────
   1 │ M        180
   2 │ F        175
- Modality 3 / 4
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ weight
     │ Int64
─────┼────────
   1 │     80
   2 │     60
- Modality 4 / 4
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ age    sex
     │ Int64  Char
─────┼─────────────
   1 │    25  M
   2 │    26  F

julia> dropmodalities!(md, [2,3])
[ Info: 変数 3 はモダリティ 2 の最後の変数でした: モダリティを削除しています
[ Info: 変数 3 はモダリティ 2 の最後の変数でした: モダリティを削除しています
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ name    age
     │ String  Int64
─────┼───────────────
   1 │ Python     25
   2 │ Julia      26
- Modality 2 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    25
   2 │    26

julia> dropmodalities!(md, 2)
[ Info: 変数 2 はモダリティ 2 の最後の変数でした: モダリティを削除しています
● MultiDataset
   └─ dimensionalities: (0,)
- Modality 1 / 1
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
```
