```
Titanic(; as_df = true, dir = nothing)
```

The Titanic dataset, describing the survival of passengers on the Titanic ship.

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
julia> using MLDatasets: Titanic

julia> using DataFrames

julia> dataset = Titanic()
Titanic:
  metadata => Dict{String, Any} with 5 entries
  features => 891×11 DataFrame
  targets => 891×1 DataFrame
  dataframe => 891×12 DataFrame


julia> describe(dataset.dataframe)
12×7 DataFrame
 Row │ variable     mean      min                  median   max                          nmissing  eltype                   
     │ Symbol       Union…    Any                  Union…   Any                          Int64     Type                     
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ PassengerId  446.0     1                    446.0    891                                 0  Int64
   2 │ Survived     0.383838  0                    0.0      1                                   0  Int64
   3 │ Pclass       2.30864   1                    3.0      3                                   0  Int64
   4 │ Name                   Abbing, Mr. Anthony           van Melkebeke, Mr. Philemon         0  String
   5 │ Sex                    female                        male                                0  String7
   6 │ Age          29.6991   0.42                 28.0     80.0                              177  Union{Missing, Float64}
   7 │ SibSp        0.523008  0                    0.0      8                                   0  Int64
   8 │ Parch        0.381594  0                    0.0      6                                   0  Int64
   9 │ Ticket                 110152                        WE/P 5735                           0  String31
  10 │ Fare         32.2042   0.0                  14.4542  512.329                             0  Float64
  11 │ Cabin                  A10                           T                                 687  Union{Missing, String15}
  12 │ Embarked               C                             S                                   2  Union{Missing, String1}
```
