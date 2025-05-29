```
variableindex(df, variable_name)
variableindex(md, i_modality, variable_name)
variableindex(md, variable_name)
```

変数のインデックスを返します。`i_modality`が渡されると、関数は`i_modality`によって識別されたモダリティのサブデータフレーム内の変数のインデックスを返します。変数が`i_modality`によって識別されたモダリティに含まれていない場合は`0`を返します。

# 引数

  * `df`は`AbstractDataFrame`です；
  * `md`は`AbstractMultiDataset`です；
  * `variable_name`はインデックスを知りたい変数を示す`Symbol`です；
  * `i_modality`はどのモダリティの変数のインデックスを知りたいかを示す`Integer`です。

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

julia> md.data
2×3 DataFrame
 Row │ name    age    sex
     │ String  Int64  Char
─────┼─────────────────────
   1 │ Python     25  M
   2 │ Julia      26  F

julia> variableindex(md, :age)
2

julia> variableindex(md, :sex)
3

julia> variableindex(md, 1, :name)
1

julia> variableindex(md, 2, :name)
0

julia> variableindex(md, 2, :sex)
1

julia> variableindex(md.data, :age)
2
```
