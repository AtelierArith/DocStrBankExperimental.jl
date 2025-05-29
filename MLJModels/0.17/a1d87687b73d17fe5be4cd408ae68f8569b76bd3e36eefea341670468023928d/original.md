```
FillImputer
```

A model type for constructing a fill imputer, based on [MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
FillImputer = @load FillImputer pkg=MLJModels
```

Do `model = FillImputer()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `FillImputer(features=...)`.

Use this model to impute `missing` values in tabular data. A fixed "filler" value is learned from the training data, one for each column of the table.

For imputing missing values in a vector, use [`UnivariateFillImputer`](@ref) instead.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X)
```

where

  * `X`: any table of input features (eg, a `DataFrame`) whose columns each have element scitypes `Union{Missing, T}`, where `T` is a subtype of `Continuous`, `Multiclass`, `OrderedFactor` or `Count`. Check scitypes with `schema(X)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `features`: a vector of names of features (symbols) for which imputation is to be attempted; default is empty, which is interpreted as "impute all".
  * `continuous_fill`: function or other callable to determine value to be imputed in the case of `Continuous` (abstract float) data; default is to apply `median` after skipping `missing` values
  * `count_fill`: function or other callable to determine value to be imputed in the case of `Count` (integer) data; default is to apply rounded `median` after skipping `missing` values
  * `finite_fill`: function or other callable to determine value to be imputed in the case of `Multiclass` or `OrderedFactor` data (categorical vectors); default is to apply `mode` after skipping `missing` values

# Operations

  * `transform(mach, Xnew)`: return `Xnew` with missing values imputed with the fill values learned when fitting `mach`

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `features_seen_in_fit`: the names of features (columns) encountered during training
  * `univariate_transformer`: the univariate model applied to determine   the fillers (it's fields contain the functions defining the filler computations)
  * `filler_given_feature`: dictionary of filler values, keyed on feature (column) names

# Examples

```
using MLJ
imputer = FillImputer()

X = (a = [1.0, 2.0, missing, 3.0, missing],
     b = coerce(["y", "n", "y", missing, "y"], Multiclass),
     c = [1, 1, 2, missing, 3])

schema(X)
julia> schema(X)
┌───────┬───────────────────────────────┐
│ names │ scitypes                      │
├───────┼───────────────────────────────┤
│ a     │ Union{Missing, Continuous}    │
│ b     │ Union{Missing, Multiclass{2}} │
│ c     │ Union{Missing, Count}         │
└───────┴───────────────────────────────┘

mach = machine(imputer, X)
fit!(mach)

julia> fitted_params(mach).filler_given_feature
(filler = 2.0,)

julia> fitted_params(mach).filler_given_feature
Dict{Symbol, Any} with 3 entries:
  :a => 2.0
  :b => "y"
  :c => 2

julia> transform(mach, X)
(a = [1.0, 2.0, 2.0, 3.0, 2.0],
 b = CategoricalValue{String, UInt32}["y", "n", "y", "y", "y"],
 c = [1, 1, 2, 2, 3],)
```

See also [`UnivariateFillImputer`](@ref).
