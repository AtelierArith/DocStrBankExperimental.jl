```
variableindex(df, variable_name)
variableindex(md, i_modality, variable_name)
variableindex(md, variable_name)
```

Return the index of the variable. When `i_modality` is passed, the function  returns the index of the variable in the sub-dataframe of the modality identified by `i_modality`. It returns `0` when the variable is not contained in the modality identified by `i_modality`.

# Arguments

  * `df` is an `AbstractDataFrame`;
  * `md` is an `AbstractMultiDataset`;
  * `variable_name` is a `Symbol` indicating the variable whose index you want to know;
  * `i_modality` is an `Integer` indicating of which modality you want to know the index of   the variable.

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
