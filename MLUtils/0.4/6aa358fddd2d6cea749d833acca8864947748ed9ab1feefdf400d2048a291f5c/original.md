```
undersample([rng], data, classes; shuffle=true)
undersample([rng], data::Tuple; shuffle=true)
```

Generate a class-balanced version of `data` by subsampling its observations in such a way that the resulting number of observations will be the same number for every class. This way, all classes will have as many observations in the resulting data set as the smallest class has in the given (original) `data`.

The convenience parameter `shuffle` determines if the resulting data will be shuffled after its creation; if it is not shuffled then all the observations will be in their original order. Defaults to `false`.

If `data` is a tuple and `classes` is not given,  then it will be assumed that the last element of the tuple contains the classes.

The output will contain both the resampled data and classes.

```julia
# 6 observations with 3 features each
X = rand(3, 6)
# 2 classes, severely imbalanced
Y = ["a", "b", "b", "b", "b", "a"]

# subsample the class "b" to match "a"
X_bal, Y_bal = undersample(X, Y)

# this results in a smaller dataset
@assert size(X_bal) == (3,4)
@assert length(Y_bal) == 4

# now both "a", and "b" have 2 observations each
@assert sum(Y_bal .== "a") == 2
@assert sum(Y_bal .== "b") == 2
```

For this function to work, the type of `data` must implement [`numobs`](@ref) and [`getobs`](@ref). 

Note that if `data` is a tuple, then it will be assumed that the last element of the tuple contains the targets.

```julia
julia> data = DataFrame(X1=rand(6), X2=rand(6), Y=[:a,:b,:b,:b,:b,:a])
6×3 DataFrames.DataFrame
│ Row │ X1        │ X2          │ Y │
├─────┼───────────┼─────────────┼───┤
│ 1   │ 0.226582  │ 0.0443222   │ a │
│ 2   │ 0.504629  │ 0.722906    │ b │
│ 3   │ 0.933372  │ 0.812814    │ b │
│ 4   │ 0.522172  │ 0.245457    │ b │
│ 5   │ 0.505208  │ 0.11202     │ b │
│ 6   │ 0.0997825 │ 0.000341996 │ a │

julia> getobs(undersample(data, data.Y))
4×3 DataFrame
 Row │ X1        X2         Y      
     │ Float64   Float64    Symbol 
─────┼─────────────────────────────
   1 │ 0.427064  0.0648339  a
   2 │ 0.376304  0.100022   a
   3 │ 0.467095  0.185437   b
   4 │ 0.457043  0.490688   b
```

See [`ObsView`](@ref) for more information on data subsets. See also [`oversample`](@ref).
