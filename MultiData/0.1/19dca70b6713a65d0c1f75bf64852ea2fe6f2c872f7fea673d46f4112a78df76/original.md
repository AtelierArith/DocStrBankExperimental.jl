```
LabeledMultiDataset(md, labeling_variables)
```

Create a `LabeledMultiDataset` by associating an `AbstractMultiDataset` with some labeling variables, specified as a column index (`Int`) or a vector of column indices (`Vector{Int}`).

# Arguments

  * `md` is the original `AbstractMultiDataset`;
  * `labeling_variables` is an `AbstractVector` of integers indicating the indices of the   variables that will be set as labels.

# Examples

```julia-repl
julia> lmd = LabeledMultiDataset(MultiDataset([[2],[4]], DataFrame(
           :id => [1, 2],
           :age => [30, 9],
           :name => ["Python", "Julia"],
           :stat => [[sin(i) for i in 1:50000], [cos(i) for i in 1:50000]]
       )), [1, 3])
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

```
