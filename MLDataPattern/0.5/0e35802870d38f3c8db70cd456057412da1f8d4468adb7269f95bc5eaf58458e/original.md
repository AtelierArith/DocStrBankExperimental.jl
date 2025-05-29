```
undersample([f], data, [shuffle = false], [obsdim])
```

Generate a class-balanced version of `data` by subsampling its observations in such a way that the resulting number of observations will be the same number for every class. This way, all classes will have as many observations in the resulting data set as the smallest class has in the given (original) `data`.

The convenience parameter `shuffle` determines if the resulting data will be shuffled after its creation; if it is not shuffled then all the observations will be in their original order. Defaults to `false`.

The optional parameter `obsdim` can be used to specify which dimension denotes the observations, if that concept makes sense for the type of `data`. See `?ObsDim` for more information.

```julia
# 6 observations with 3 features each
X = rand(3, 6)
# 2 classes, severely imbalanced
Y = ["a", "b", "b", "b", "b", "a"]

# subsample the class "b" to match "a"
X_bal, Y_bal = undersample((X,Y))

# this results in a smaller dataset
@assert size(X_bal) == (3,4)
@assert length(Y_bal) == 4

# now both "a", and "b" have 2 observations each
@assert sum(Y_bal .== "a") == 2
@assert sum(Y_bal .== "b") == 2
```

For this function to work, the type of `data` must implement [`nobs`](@ref) and [`getobs`](@ref). For example, the following code allows `undersample` to work on a `DataTable`.

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

julia> getobs(undersample(row->row[:Y], data))
4×3 DataTables.DataTable
│ Row │ X1        │ X2          │ Y │
├─────┼───────────┼─────────────┼───┤
│ 1   │ 0.226582  │ 0.0443222   │ a │
│ 2   │ 0.504629  │ 0.722906    │ b │
│ 3   │ 0.522172  │ 0.245457    │ b │
│ 4   │ 0.0997825 │ 0.000341996 │ a │
```

see [`DataSubset`](@ref) for more information on data subsets.

see also [`oversample`](@ref) and [`stratifiedobs`](@ref).
