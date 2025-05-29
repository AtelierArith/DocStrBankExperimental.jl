```
addmodality!(md, indices)
addmodality!(md, index)
addmodality!(md, variable_names)
addmodality!(md, variable_name)
```

マルチモーダルデータセットにおいて、`indices`または`index`の変数を使用して新しいモダリティを作成し、データセット自体を返します。

`indices`および`index`の代わりに、変数名を使用することもできます。

注意: 新しい変数で新しいモダリティを追加するには、[`insertmodality!`](@ref)を参照してください。

# 引数

  * `md`は`MultiDataset`です。
  * `indices`は、マルチモーダルデータセットの対応するデータフレームのどのインデックスを新しいモダリティに追加するかを示す`AbstractVector{Integer}`です。
  * `index`は、マルチモーダルデータセットの対応するデータフレームに新しいモダリティを追加するインデックスを示す`Integer`です。
  * `variable_names`は、マルチモーダルデータセットの対応するデータフレームに新しいモダリティを追加する変数を示す`AbstractVector{Symbol}`です。
  * `variable_name`は、マルチモーダルデータセットの対応するデータフレームに新しいモダリティを追加する変数を示す`Symbol`です。

# 例

```julia-repl
julia> df = DataFrame(:name => ["Python", "Julia"], :age => [25, 26], :sex => ['M', 'F'], :height => [180, 175], :weight => [80, 60])
2×5 DataFrame
 Row │ name    age    sex   height  weight
     │ String  Int64  Char  Int64   Int64
─────┼─────────────────────────────────────
   1 │ Python     25  M        180      80
   2 │ Julia      26  F        175      60

julia> md = MultiDataset([[1]], df)
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
- Spare variables
   └─ dimensionality: 0
2×4 SubDataFrame
 Row │ age    sex   height  weight
     │ Int64  Char  Int64   Int64
─────┼─────────────────────────────
   1 │    25  M        180      80
   2 │    26  F        175      60


julia> addmodality!(md, [:age, :sex])
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Modality 2 / 2
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ age    sex
     │ Int64  Char
─────┼─────────────
   1 │    25  M
   2 │    26  F
- Spare variables
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ height  weight
     │ Int64   Int64
─────┼────────────────
   1 │    180      80
   2 │    175      60


julia> addmodality!(md, 5)
● MultiDataset
   └─ dimensionalities: (0, 0, 0)
- Modality 1 / 3
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
- Modality 2 / 3
   └─ dimensionality: 0
2×2 SubDataFrame
 Row │ age    sex
     │ Int64  Char
─────┼─────────────
   1 │    25  M
   2 │    26  F
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
```
