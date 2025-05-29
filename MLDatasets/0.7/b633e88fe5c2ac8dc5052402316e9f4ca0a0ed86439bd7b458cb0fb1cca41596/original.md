```
BostonHousing(; as_df = true, dir = nothing)
```

The classical Boston Housing tabular dataset.

Sources:    (a) Origin:  This dataset was taken from the StatLib library which is                 maintained at Carnegie Mellon University.    (b) Creator:  Harrison, D. and Rubinfeld, D.L. 'Hedonic prices and the                   demand for clean air', J. Environ. Economics & Management,                  vol.5, 81-102, 1978.    (c) Date: July 7, 1993

Number of Instances: 506

Number of Attributes: 13 continuous attributes (including target                             attribute "MEDV"), 1 binary-valued attribute.

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
julia> using MLDatasets: BostonHousing

julia> dataset = BostonHousing()
BostonHousing:
  metadata => Dict{String, Any} with 5 entries
  features => 506×13 DataFrame
  targets => 506×1 DataFrame
  dataframe => 506×14 DataFrame


julia> dataset[1:5][1]
5×13 DataFrame
 Row │ CRIM     ZN       INDUS    CHAS   NOX      RM       AGE      DIS      RAD    TAX    PTRATIO  B        LSTAT   
     │ Float64  Float64  Float64  Int64  Float64  Float64  Float64  Float64  Int64  Int64  Float64  Float64  Float64 
─────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 0.00632     18.0     2.31      0    0.538    6.575     65.2   4.09        1    296     15.3   396.9      4.98
   2 │ 0.02731      0.0     7.07      0    0.469    6.421     78.9   4.9671      2    242     17.8   396.9      9.14
   3 │ 0.02729      0.0     7.07      0    0.469    7.185     61.1   4.9671      2    242     17.8   392.83     4.03
   4 │ 0.03237      0.0     2.18      0    0.458    6.998     45.8   6.0622      3    222     18.7   394.63     2.94
   5 │ 0.06905      0.0     2.18      0    0.458    7.147     54.2   6.0622      3    222     18.7   396.9      5.33

julia> dataset[1:5][2]
5×1 DataFrame
Row │ MEDV    
    │ Float64 
────┼─────────
  1 │    24.0
  2 │    21.6
  3 │    34.7
  4 │    33.4
  5 │    36.2  

julia> X, y = BostonHousing(as_df=false)[:]
([0.00632 0.02731 … 0.10959 0.04741; 18.0 0.0 … 0.0 0.0; … ; 396.9 396.9 … 393.45 396.9; 4.98 9.14 … 6.48 7.88], [24.0 21.6 … 22.0 11.9])
```
