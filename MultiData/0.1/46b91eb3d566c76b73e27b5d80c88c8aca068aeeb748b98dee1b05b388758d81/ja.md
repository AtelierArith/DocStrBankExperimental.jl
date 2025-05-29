```
insertvariables!(md, col, index, values)
insertvariables!(md, index, values)
insertvariables!(md, col, index, value)
insertvariables!(md, index, value)
```

指定されたインデックスでマルチモーダルデータセットに変数を挿入します。

!!! note
    挿入された各変数は、予備変数として追加されます。


# 引数

  * `md` は `AbstractMultiDataset` です;
  * `col` は新しい変数を挿入する位置を示す `Integer` です。 `col` が渡されない場合、新しい変数は md の基礎となるデータフレーム構造の最後に配置されます;
  * `index` は `Symbol` で、挿入する変数の名前を示します。重複した変数名は、競合を避けるために名前が変更されます: `insertcols!` の `makeunique` 引数を参照してください [insertcols!](https://dataframes.juliadata.org/stable/lib/functions/#DataFrames.insertcols!) DataFrames ドキュメント内;
  * `values` は新しく挿入された変数の値を示す `AbstractVector` です。 `values` の長さは `ninstances(md)` と一致する必要があります;
  * `value` は新しい変数の単一の値です。単一の `value` が最後の引数として渡されると、これはコピーされ、データセット内の各インスタンスに使用されます。

# 例

```julia-repl
julia> md = MultiDataset([[1, 2],[3]], DataFrame(:name => ["Python", "Julia"], :age => [25, 26], :sex => ['M', 'F']))
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
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F

julia> insertvariables!(md, :weight, [80, 75])
2×4 DataFrame
 Row │ name    age    sex   weight
     │ String  Int64  Char  Int64
─────┼─────────────────────────────
   1 │ Python     25  M         80
   2 │ Julia      26  F         75

julia> md
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
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F
- Spare variables
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ weight
     │ Int64
─────┼────────
   1 │     80
   2 │     75

julia> insertvariables!(md, 2, :height, 180)
2×5 DataFrame
 Row │ name    height  age    sex   weight
     │ String  Int64   Int64  Char  Int64
─────┼─────────────────────────────────────
   1 │ Python     180     25  M         80
   2 │ Julia      180     26  F         75

julia> insertvariables!(md, :hair, ["brown", "blonde"])
2×6 DataFrame
 Row │ name    height  age    sex   weight  hair
     │ String  Int64   Int64  Char  Int64   String
─────┼─────────────────────────────────────────────
   1 │ Python     180     25  M         80  brown
   2 │ Julia      180     26  F         75  blonde

julia> md
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
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F
- Spare variables
   └─ dimensionality: 0
2×3 SubDataFrame
 Row │ height  weight  hair
     │ Int64   Int64   String
─────┼────────────────────────
   1 │    180      80  brown
   2 │    180      75  blonde
```
