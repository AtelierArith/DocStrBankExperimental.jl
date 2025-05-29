```
nvariables(md)
nvariables(md, i)
```

Return the number of variables in a multimodal dataset.

If an index `i` is passed as second argument, then the number of variables of the `i`-th modality is returned.

Alternatively, `nvariables` can be called on a single modality.

# Arguments

  * `md` is a `MultiDataset`;
  * `i` (optional) is an `Integer` indicating the modality of the multimodal dataset whose   number of variables you want to know.

# Examples

```julia-repl
julia> md = MultiDataset([[1],[2]], DataFrame(:age => [25, 26], :sex => ['M', 'F']))
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


julia> nvariables(md)
2

julia> nvariables(md, 2)
1

julia> mod2 = modality(md, 2)
2×1 SubDataFrame
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F

julia> nvariables(mod2)
1

julia> md = MultiDataset([[1, 2],[3, 4, 5]], DataFrame(:name => ["Python", "Julia"], :age => [25, 26], :sex => ['M', 'F'], :height => [180, 175], :weight => [80, 60]))
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
2×3 SubDataFrame
 Row │ sex   height  weight
     │ Char  Int64   Int64
─────┼──────────────────────
   1 │ M        180      80
   2 │ F        175      60

julia> nvariables(md)
5

julia> nvariables(md, 2)
3

julia> mod2 = modality(md,2)
2×3 SubDataFrame
 Row │ sex   height  weight
     │ Char  Int64   Int64
─────┼──────────────────────
   1 │ M        180      80
   2 │ F        175      60

julia> nvariables(mod2)
3
```
