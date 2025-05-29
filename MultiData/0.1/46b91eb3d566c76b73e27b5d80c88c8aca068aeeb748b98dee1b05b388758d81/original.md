```
insertvariables!(md, col, index, values)
insertvariables!(md, index, values)
insertvariables!(md, col, index, value)
insertvariables!(md, index, value)
```

Insert a variable in a multimodal dataset with a given index.

!!! note
    Each inserted variable will be added in as a spare variables.


# Arguments

  * `md` is an `AbstractMultiDataset`;
  * `col` is an `Integer` indicating in which position to insert the new variable.   If no col is passed, the new variable will be placed   last in the md's underlying dataframe structure;
  * `index` is a `Symbol` and denote the name of the variable to insert.   Duplicated variable names will be renamed to avoid conflicts: see `makeunique` argument   for [insertcols!](https://dataframes.juliadata.org/stable/lib/functions/#DataFrames.insertcols!)   in DataFrames documentation;
  * `values` is an `AbstractVector` that indicates the values for the newly   inserted variable. The length of `values` should match `ninstances(md)`;
  * `value` is a single value for the new variable. If a single `value` is passed as a last   argument this will be copied and used for each instance in the dataset.

# Examples

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
