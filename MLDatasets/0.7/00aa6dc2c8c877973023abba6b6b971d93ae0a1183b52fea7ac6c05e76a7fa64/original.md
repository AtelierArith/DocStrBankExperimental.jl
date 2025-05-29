```
Iris(; as_df = true, dir = nothing)
```

Fisher's classic iris dataset. 

Measurements from 3 different species of iris: setosa, versicolor and virginica. There are 50 examples of each species.

There are 4 measurements for each example: sepal length, sepal width, petal length and petal width.  The measurements are in centimeters.

The module retrieves the data from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/iris).

NOTE: no pre-defined train-test split for this dataset. 

# Arguments

  * If `as_df = true`, load the data as dataframes instead of plain arrays.
  * You can pass a specific `dir` where to load or download the dataset, otherwise uses the default one.

# Fields

  * `metadata`: A dictionary containing additional information on the dataset.
  * `features`: The data features. An array if `as_df=false`, otherwise a dataframe.
  * `targets`: The targets for supervised learning. An array if `as_df=false`, otherwise a dataframe.
  * `dataframe`: A dataframe containing both `features` and `targets`. It is `nothing` if `as_df=false`, otherwise a dataframed.

# Methods

  * `dataset[i]`: Return observation(s) `i` as a named tuple of features and targets.
  * `dataset[:]`: Return all observations as a named tuple of features and targets.
  * `length(dataset)`: Number of observations.

# Examples

```julia-repl
julia> dataset = Iris()
Iris:
  metadata => Dict{String, Any} with 4 entries
  features => 150×4 DataFrame
  targets => 150×1 DataFrame
  dataframe => 150×5 DataFrame


julia> dataset[1:2]
(2×4 DataFrame
 Row │ sepallength  sepalwidth  petallength  petalwidth 
     │ Float64      Float64     Float64      Float64    
─────┼──────────────────────────────────────────────────
   1 │         5.1         3.5          1.4         0.2
   2 │         4.9         3.0          1.4         0.2, 2×1 DataFrame
 Row │ class       
     │ String15    
─────┼─────────────
   1 │ Iris-setosa
   2 │ Iris-setosa)

julia> X, y = Iris(as_df=false)[:]
([5.1 4.9 … 6.2 5.9; 3.5 3.0 … 3.4 3.0; 1.4 1.4 … 5.4 5.1; 0.2 0.2 … 2.3 1.8], InlineStrings.String15["Iris-setosa" "Iris-setosa" … "Iris-virginica" "Iris-virginica"])
```
