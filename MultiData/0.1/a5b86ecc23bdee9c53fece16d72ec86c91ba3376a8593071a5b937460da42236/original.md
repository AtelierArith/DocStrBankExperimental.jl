```
loaddataset(datasetpath; onlywithlabels = [], shufflelabels = [], rng = Random.GLOBAL_RNG)
```

Create a `MultiDataset` or a `LabeledMultiDataset` from a Dataset, based on the presence of file Labels.csv.

# Arguments

  * `datasetpath` is an `AbstractString` that denote the Dataset's position;
  * `onlywithlabels` is an AbstractVector{AbstractVector{Pair{AbstractString,AbstractVector{Any}}}}   and it's used to select which portion of the Dataset to load, by specifying labels and   their values.   Beginning from the center, each Pair{AbstractString,AbstractVector{Any}} must contain,   as AbstractString the label's name, and, as AbstractVector{Any} the values for that label.   Each Pair in one vector must refer to a different label, so if the Dataset has in total   n labels, this vector of Pair can contain maximun n element. That's because the elements   will combine with each other.   Every vector of Pair act as a filter.   Note that the same label can be used in different vector of Pair as they do not combine   with each other.   If `onlywithlabels` is an empty vector (default) the function will load the entire   Dataset.
  * `shufflelabels` is an `AbstractVector` of names of labels to shuffle (default = [], means   no shuffle).
  * `rng` is a random number generator to be used when shuffling (for reproducibility); can be   either a Integer (used as seed for `MersenneTwister`) or an `AbstractRNG`.

# Examples

```julia-repl
julia> df_data = DataFrame(
           :id => [1, 2, 3, 4, 5],
           :age => [30, 9, 30, 40, 9],
           :name => ["Python", "Julia", "C", "Java", "R"],
           :stat => [deepcopy(ts_sin), deepcopy(ts_cos), deepcopy(ts_sin), deepcopy(ts_cos), deepcopy(ts_sin)]
       )
5×4 DataFrame
 Row │ id     age    name    stat
     │ Int64  Int64  String  Array…
─────┼─────────────────────────────────────────────────────────
   1 │     1     30  Python  [0.841471, 0.909297, 0.14112, -0…
   2 │     2      9  Julia   [0.540302, -0.416147, -0.989992,…
   3 │     3     30  C       [0.841471, 0.909297, 0.14112, -0…
   4 │     4     40  Java    [0.540302, -0.416147, -0.989992,…
   5 │     5      9  R       [0.841471, 0.909297, 0.14112, -0…

julia> lmd = LabeledMultiDataset(
    MultiDataset([[4]], deepcopy(df_data)),
    [2,3],
)
● LabeledMultiDataset
   ├─ labels
   │   ├─ age: Set([9, 30, 40])
   │   └─ name: Set(["C", "Julia", "Python", "Java", "R"])
   └─ dimensionalities: (1,)
- Modality 1 / 1
   └─ dimensionality: 1
5×1 SubDataFrame
 Row │ stat
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.841471, 0.909297, 0.14112, -0…
   2 │ [0.540302, -0.416147, -0.989992,…
   3 │ [0.841471, 0.909297, 0.14112, -0…
   4 │ [0.540302, -0.416147, -0.989992,…
   5 │ [0.841471, 0.909297, 0.14112, -0…
- Spare variables
   └─ dimensionality: 0
5×1 SubDataFrame
 Row │ id
     │ Int64
─────┼───────
   1 │     1
   2 │     2
   3 │     3
   4 │     4
   5 │     5

julia> savedataset("langs", lmd, force = true)

julia> loaddataset("langs", onlywithlabels = [ ["name" => ["Julia"], "age" => ["9"]] ] )
Instances count: 1
Total size: 981670 bytes
● LabeledMultiDataset
   ├─ labels
   │   ├─ age: Set(["9"])
   │   └─ name: Set(["Julia"])
   └─ dimensionalities: (1,)
- Modality 1 / 1
   └─ dimensionality: 1
1×1 SubDataFrame
 Row │ stat
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.540302, -0.416147, -0.989992,…
- Spare variables
   └─ dimensionality: 0
1×1 SubDataFrame
 Row │ id
     │ Int64
─────┼───────
   1 │     2

julia> loaddataset("langs", onlywithlabels = [ ["name" => ["Julia"], "age" => ["30"]] ] )
Instances count: 0
Total size: 0 bytes
ERROR: AssertionError: No instance found

julia> loaddataset("langs", onlywithlabels = [ ["name" => ["Julia"]] , ["age" => ["9"]] ] )
Instances count: 2
Total size: 1963537 bytes
● LabeledMultiDataset
   ├─ labels
   │   ├─ age: Set(["9"])
   │   └─ name: Set(["Julia", "R"])
   └─ dimensionalities: (1,)
- Modality 1 / 1
   └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.540302, -0.416147, -0.989992,…
   2 │ [0.841471, 0.909297, 0.14112, -0…
- Spare variables
   └─ dimensionality: 0
2×1 SubDataFrame
 Row │ id
     │ Int64
─────┼───────
   1 │     2
   2 │     5

julia> loaddataset("langs", onlywithlabels = [ ["name" => ["Julia"]], ["name" => ["C"], "age" => ["30"]] ] )
Instances count: 2
Total size: 1963537 bytes
● LabeledMultiDataset
    ├─ labels
    │   ├─ age: Set(["9", "30"])
    │   └─ name: Set(["C", "Julia"])
    └─ dimensionalities: (1,)
- Modality 1 / 1
    └─ dimensionality: 1
2×1 SubDataFrame
 Row │ stat
     │ Array…
─────┼───────────────────────────────────
   1 │ [0.540302, -0.416147, -0.989992,…
   2 │ [0.841471, 0.909297, 0.14112, -0…
- Spare variables
    └─ dimensionality: 0
2×1 SubDataFrame
 Row │ id
     │ Int64
─────┼───────
   1 │     2
   2 │     3
```
