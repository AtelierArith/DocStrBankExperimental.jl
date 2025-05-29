```
variables(md, i)
```

Return the names as `Symbol`s of the variables in a multimodal dataset.

When called on a object of type `MultiDataset` a `Dict` is returned which will map the modality index to an `AbstractVector{Symbol}`.

Note: the order of the variable names is granted to match the order of the variables in the modality.

If an index `i` is passed as second argument, then the names of the variables of the `i`-th modality are returned as an `AbstractVector`.

Alternatively, `nvariables` can be called on a single modality.

# Arguments

  * `md` is an MultiDataset;
  * `i` is an `Integer` indicating from which modality of the multimodal dataset to get the   names of the variables.

# Examples

```julia-repl
julia> md = MultiDataset([[2],[3]], DataFrame(:name => ["Python", "Julia"], :age => [25, 26], :sex => ['M', 'F']))
● MultiDataset
   └─ dimensionalities: (0, 0)
- Modality 1 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    25
   2 │    26
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
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia

julia> variables(md)
Dict{Integer, AbstractVector{Symbol}} with 2 entries:
  2 => [:sex]
  1 => [:age]

julia> variables(md, 2)
1-element Vector{Symbol}:
 :sex

julia> variables(md, 1)
1-element Vector{Symbol}:
 :age

julia> mod2 = modality(md, 2)
2×1 SubDataFrame
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F

julia> variables(mod2)
1-element Vector{Symbol}:
 :sex
```
