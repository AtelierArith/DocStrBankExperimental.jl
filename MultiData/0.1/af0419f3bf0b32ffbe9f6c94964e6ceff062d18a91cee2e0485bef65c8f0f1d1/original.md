```
joinlabels!(lmd, [lbls...]; delim = "_")
```

On a labeled multimodal dataset, collapse the labeling variables identified by `lbls` into a single labeling variable of type `String`, by means of a `join` that uses `delim` for string delimiter.

If not specified differently this function will join all labels.

`lbls` can be an `Integer` indicating the index of the label, or a `Symbol` indicating the name of the labeling variable.

# !!! note

# The resulting labels will always be of type `String`.

!!! note
    The resulting labeling variable will always be added as last column in the underlying `DataFrame`.


# Examples

```julia-repl
julia> lmd = LabeledMultiDataset(
           MultiDataset(
               [[2],[4]],
               DataFrame(
                   :id => [1, 2],
                   :age => [30, 9],
                   :name => ["Python", "Julia"],
                   :stat => [[sin(i) for i in 1:50000], [cos(i) for i in 1:50000]]
               )
           ),
           [1, 3],
       )
● LabeledMultiDataset
   ├─ labels
   │   ├─ id: Set([2, 1])
   │   └─ name: Set(["Julia", "Python"])
   └─ dimensionalities: (0, 1)
- Modality 1 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    30
   2 │     9
- Modality 2 / 2
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…


julia> joinlabels!(lmd)
● LabeledMultiDataset
   ├─ labels
   │   └─ id_name: Set(["1_Python", "2_Julia"])
   └─ dimensionalities: (0, 1)
- Modality 1 / 2
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    30
   2 │     9
- Modality 2 / 2
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…
```
