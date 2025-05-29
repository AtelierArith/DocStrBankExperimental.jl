```
hasvariables(df, variable_name)
hasvariables(md, i_modality, variable_name)
hasvariables(md, variable_name)
hasvariables(df, variable_names)
hasvariables(md, i_modality, variable_names)
hasvariables(md, variable_names)
```

Check whether a multimodal dataset contains a variable named `variable_name`.

Instead of a single variable name a `Vector` of names can be passed. If this is the case, this function will return `true` only if `md` contains all the specified variables.

# Arguments

  * `df` is an `AbstractDataFrame`, which is one of the two structure in which you want to check   the presence of the variable;
  * `md` is an `AbstractMultiDataset`, which is one of the two structure in which you want   to check the presence of the variable;
  * `variable_name` is a `Symbol` indicating the variable, whose existence I want to   verify;
  * `i_modality` is an `Integer` indicating in which modality to look for the variable.

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
