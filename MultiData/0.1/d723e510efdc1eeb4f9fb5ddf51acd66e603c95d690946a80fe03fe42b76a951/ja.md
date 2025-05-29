```
hasvariables(df, variable_name)
hasvariables(md, i_modality, variable_name)
hasvariables(md, variable_name)
hasvariables(df, variable_names)
hasvariables(md, i_modality, variable_names)
hasvariables(md, variable_names)
```

マルチモーダルデータセットに `variable_name` という名前の変数が含まれているかどうかを確認します。

単一の変数名の代わりに、名前の `Vector` を渡すことができます。この場合、この関数は `md` が指定されたすべての変数を含む場合にのみ `true` を返します。

# 引数

  * `df` は `AbstractDataFrame` であり、変数の存在を確認したい2つの構造のうちの1つです；
  * `md` は `AbstractMultiDataset` であり、変数の存在を確認したい2つの構造のうちの1つです；
  * `variable_name` は、存在を確認したい変数を示す `Symbol` です；
  * `i_modality` は、変数を探すモダリティを示す `Integer` です。

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

julia> hasvariables(md, :age)
true

julia> hasvariables(md.data, :name)
true

julia> hasvariables(md, :height)
false

julia> hasvariables(md, 1, :sex)
false

julia> hasvariables(md, 2, :sex)
true
```

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

julia> hasvariables(md, [:sex, :age])
true

julia> hasvariables(md, 1, [:sex])
false

julia> hasvariables(md, 2, [:sex])
true

julia> hasvariables(md.data, [:name, :sex])
true
```
