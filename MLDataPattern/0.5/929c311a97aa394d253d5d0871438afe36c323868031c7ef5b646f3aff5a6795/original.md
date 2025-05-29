```
oversample([f], data, [fraction = 1], [shuffle = true], [obsdim])
```

Generate a re-balanced version of `data` by repeatedly sampling existing observations in such a way that every class will have at least `fraction` times the number observations of the largest class. This way, all classes will have a minimum number of observations in the resulting data set relative to what largest class has in the given (original) `data`.

As an example, by default (i.e. with `fraction = 1`) the resulting dataset will be near perfectly balanced. On the other hand, with `fraction = 0.5` every class in the resulting data with have at least 50% as many observations as the largest class.

The convenience parameter `shuffle` determines if the resulting data will be shuffled after its creation; if it is not shuffled then all the repeated samples will be together at the end, sorted by class. Defaults to `true`.

The optional parameter `obsdim` can be used to specify which dimension denotes the observations, if that concept makes sense for the type of `data`. See `?ObsDim` for more information.

```julia
# 6 observations with 3 features each
X = rand(3, 6)
# 2 classes, severely imbalanced
Y = ["a", "b", "b", "b", "b", "a"]

# oversample the class "a" to match "b"
X_bal, Y_bal = oversample((X,Y))

# this results in a bigger dataset with repeated data
@assert size(X_bal) == (3,8)
@assert length(Y_bal) == 8

# now both "a", and "b" have 4 observations each
@assert sum(Y_bal .== "a") == 4
@assert sum(Y_bal .== "b") == 4
```

For this function to work, the type of `data` must implement [`nobs`](@ref) and [`getobs`](@ref). For example, the following code allows `oversample` to work on a `DataTable`.

```julia
# Make DataTables.jl work
LearnBase.getobs(data::DataTable, i) = data[i,:]
StatsBase.nobs(data::DataTable) = nrow(data)
```

You can use the parameter `f` to specify how to extract or retrieve the targets from each observation of the given `data`. Note that if `data` is a tuple, then it will be assumed that the last element of the tuple contains the targets and `f` will be applied to each observation in that element.

```julia
julia> data = DataTable(Any[rand(6), rand(6), [:a,:b,:b,:b,:b,:a]], [:X1,:X2,:Y])
6×3 DataTables.DataTable
│ Row │ X1        │ X2          │ Y │
├─────┼───────────┼─────────────┼───┤
│ 1   │ 0.226582  │ 0.0443222   │ a │
│ 2   │ 0.504629  │ 0.722906    │ b │
│ 3   │ 0.933372  │ 0.812814    │ b │
│ 4   │ 0.522172  │ 0.245457    │ b │
│ 5   │ 0.505208  │ 0.11202     │ b │
│ 6   │ 0.0997825 │ 0.000341996 │ a │

julia> getobs(oversample(row->row[:Y], data))
8×3 DataTables.DataTable
│ Row │ X1        │ X2          │ Y │
├─────┼───────────┼─────────────┼───┤
│ 1   │ 0.0997825 │ 0.000341996 │ a │
│ 2   │ 0.505208  │ 0.11202     │ b │
│ 3   │ 0.226582  │ 0.0443222   │ a │
│ 4   │ 0.0997825 │ 0.000341996 │ a │
│ 5   │ 0.504629  │ 0.722906    │ b │
│ 6   │ 0.522172  │ 0.245457    │ b │
│ 7   │ 0.226582  │ 0.0443222   │ a │
│ 8   │ 0.933372  │ 0.812814    │ b │
```

see [`DataSubset`](@ref) for more information on data subsets.

see also [`undersample`](@ref) and [`stratifiedobs`](@ref).
