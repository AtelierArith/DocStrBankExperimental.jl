```
dropsparevariables!(md)
```

Drop all variables that are not contained in any of the modalities in a multimodal dataset.

# Arguments

  * `md` is a `MultiDataset`, that is the structure at which sparevariables will be   dropped.

# Examples

```julia-repl
julia> md = MultiDataset([[1]], DataFrame(:age => [30, 9], :name => ["Python", "Julia"]))
● MultiDataset
   └─ dimensionalities: (0,)
- Modality 1 / 1
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    30
   2 │     9
- Spare variables
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia


julia> dropsparevariables!(md)
2×1 DataFrame
 Row │ name
     │ String
─────┼────────
   1 │ Python
   2 │ Julia
```
