```
oversample([rng], data, classes; fraction=1, shuffle=true)
oversample([rng], data::Tuple; fraction=1, shuffle=true)
```

Generate a re-balanced version of `data` by repeatedly sampling existing observations in such a way that every class will have at least `fraction` times the number observations of the largest class in `classes`. This way, all classes will have a minimum number of observations in the resulting data set relative to what largest class has in the given (original) `data`.

As an example, by default (i.e. with `fraction = 1`) the resulting dataset will be near perfectly balanced. On the other hand, with `fraction = 0.5` every class in the resulting data with have at least 50% as many observations as the largest class.

The `classes` input is an array with the same length as `numobs(data)`.  

The convenience parameter `shuffle` determines if the resulting data will be shuffled after its creation; if it is not shuffled then all the repeated samples will be together at the end, sorted by class. Defaults to `true`.

The random number generator `rng` can be optionally passed as the first argument. 

The output will contain both the resampled data and classes.

```julia
# 6 observations with 3 features each
X = rand(3, 6)
# 2 classes, severely imbalanced
Y = ["a", "b", "b", "b", "b", "a"]

# oversample the class "a" to match "b"
X_bal, Y_bal = oversample(X, Y)

# this results in a bigger dataset with repeated data
@assert size(X_bal) == (3,8)
@assert length(Y_bal) == 8

# now both "a", and "b" have 4 observations each
@assert sum(Y_bal .== "a") == 4
@assert sum(Y_bal .== "b") == 4
```

For this function to work, the type of `data` must implement [`numobs`](@ref) and [`getobs`](@ref). 

If `data` is a tuple and `classes` is not given,  then it will be assumed that the last element of the tuple contains the classes.

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

julia> getobs(oversample(data, data.Y))
8×3 DataFrame
 Row │ X1        X2         Y      
     │ Float64   Float64    Symbol 
─────┼─────────────────────────────
   1 │ 0.376304  0.100022   a
   2 │ 0.467095  0.185437   b
   3 │ 0.481957  0.319906   b
   4 │ 0.336762  0.390811   b
   5 │ 0.376304  0.100022   a
   6 │ 0.427064  0.0648339  a
   7 │ 0.427064  0.0648339  a
   8 │ 0.457043  0.490688   b
```

See [`ObsView`](@ref) for more information on data subsets. See also [`undersample`](@ref).
