```
OneHotEncoder
```

A model type for constructing a one-hot encoder, based on [MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
OneHotEncoder = @load OneHotEncoder pkg=MLJModels
```

Do `model = OneHotEncoder()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `OneHotEncoder(features=...)`.

Use this model to one-hot encode the `Multiclass` and `OrderedFactor` features (columns) of some table, leaving other columns unchanged.

New data to be transformed may lack features present in the fit data, but no *new* features can be present.

**Warning:** This transformer assumes that `levels(col)` for any `Multiclass` or `OrderedFactor` column, `col`, is the same for training data and new data to be transformed.

To ensure *all* features are transformed into `Continuous` features, or dropped, use [`ContinuousEncoder`](@ref) instead.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X)
```

where

  * `X`: any Tables.jl compatible table. Columns can be of mixed type but only those with element scitype `Multiclass` or `OrderedFactor` can be encoded. Check column scitypes with `schema(X)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `features`: a vector of symbols (column names). If empty (default) then all `Multiclass` and `OrderedFactor` features are encoded. Otherwise, encoding is further restricted to the specified features (`ignore=false`) or the unspecified features (`ignore=true`). This default behavior can be modified by the `ordered_factor` flag.
  * `ordered_factor=false`: when `true`, `OrderedFactor` features are universally excluded
  * `drop_last=true`: whether to drop the column corresponding to the final class of encoded features. For example, a three-class feature is spawned into three new features if `drop_last=false`, but just two features otherwise.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `all_features`: names of all features encountered in training
  * `fitted_levels_given_feature`: dictionary of the levels associated with each feature encoded, keyed on the feature name
  * `ref_name_pairs_given_feature`: dictionary of pairs `r => ftr` (such as `0x00000001 => :grad__A`) where `r` is a CategoricalArrays.jl reference integer representing a level, and `ftr` the corresponding new feature name; the dictionary is keyed on the names of features that are encoded

# Report

The fields of `report(mach)` are:

  * `features_to_be_encoded`: names of input features to be encoded
  * `new_features`: names of all output features

# Example

```
using MLJ

X = (name=categorical(["Danesh", "Lee", "Mary", "John"]),
     grade=categorical(["A", "B", "A", "C"], ordered=true),
     height=[1.85, 1.67, 1.5, 1.67],
     n_devices=[3, 2, 4, 3])

julia> schema(X)
┌───────────┬──────────────────┐
│ names     │ scitypes         │
├───────────┼──────────────────┤
│ name      │ Multiclass{4}    │
│ grade     │ OrderedFactor{3} │
│ height    │ Continuous       │
│ n_devices │ Count            │
└───────────┴──────────────────┘

hot = OneHotEncoder(drop_last=true)
mach = fit!(machine(hot, X))
W = transform(mach, X)

julia> schema(W)
┌──────────────┬────────────┐
│ names        │ scitypes   │
├──────────────┼────────────┤
│ name__Danesh │ Continuous │
│ name__John   │ Continuous │
│ name__Lee    │ Continuous │
│ grade__A     │ Continuous │
│ grade__B     │ Continuous │
│ height       │ Continuous │
│ n_devices    │ Count      │
└──────────────┴────────────┘
```

See also [`ContinuousEncoder`](@ref).
