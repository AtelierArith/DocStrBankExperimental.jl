```
ContinuousEncoder
```

A model type for constructing a continuous encoder, based on [MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
ContinuousEncoder = @load ContinuousEncoder pkg=MLJModels
```

Do `model = ContinuousEncoder()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `ContinuousEncoder(drop_last=...)`.

Use this model to arrange all features (columns) of a table to have `Continuous` element scitype, by applying the following protocol to each feature `ftr`:

  * If `ftr` is already `Continuous` retain it.
  * If `ftr` is `Multiclass`, one-hot encode it.
  * If `ftr` is `OrderedFactor`, replace it with `coerce(ftr, Continuous)` (vector of floating point integers), unless `ordered_factors=false` is specified, in which case one-hot encode it.
  * If `ftr` is `Count`, replace it with `coerce(ftr, Continuous)`.
  * If `ftr` has some other element scitype, or was not observed in fitting the encoder, drop it from the table.

**Warning:** This transformer assumes that `levels(col)` for any `Multiclass` or `OrderedFactor` column, `col`, is the same for training data and new data to be transformed.

To selectively one-hot-encode categorical features (without dropping columns) use [`OneHotEncoder`](@ref) instead.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X)
```

where

  * `X`: any Tables.jl compatible table. Columns can be of mixed type but only those with element scitype `Multiclass` or `OrderedFactor` can be encoded. Check column scitypes with `schema(X)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `drop_last=true`: whether to drop the column corresponding to the final class of one-hot encoded features. For example, a three-class feature is spawned into three new features if `drop_last=false`, but two just features otherwise.
  * `one_hot_ordered_factors=false`: whether to one-hot any feature with `OrderedFactor` element scitype, or to instead coerce it directly to a (single) `Continuous` feature using the order

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `features_to_keep`: names of features that will not be dropped from the table
  * `one_hot_encoder`: the `OneHotEncoder` model instance for handling the one-hot encoding
  * `one_hot_encoder_fitresult`: the fitted parameters of the `OneHotEncoder` model

# Report

  * `features_to_keep`: names of input features that will not be dropped from the table
  * `new_features`: names of all output features

# Example

```julia
X = (name=categorical(["Danesh", "Lee", "Mary", "John"]),
     grade=categorical(["A", "B", "A", "C"], ordered=true),
     height=[1.85, 1.67, 1.5, 1.67],
     n_devices=[3, 2, 4, 3],
     comments=["the force", "be", "with you", "too"])

julia> schema(X)
┌───────────┬──────────────────┐
│ names     │ scitypes         │
├───────────┼──────────────────┤
│ name      │ Multiclass{4}    │
│ grade     │ OrderedFactor{3} │
│ height    │ Continuous       │
│ n_devices │ Count            │
│ comments  │ Textual          │
└───────────┴──────────────────┘

encoder = ContinuousEncoder(drop_last=true)
mach = fit!(machine(encoder, X))
W = transform(mach, X)

julia> schema(W)
┌──────────────┬────────────┐
│ names        │ scitypes   │
├──────────────┼────────────┤
│ name__Danesh │ Continuous │
│ name__John   │ Continuous │
│ name__Lee    │ Continuous │
│ grade        │ Continuous │
│ height       │ Continuous │
│ n_devices    │ Continuous │
└──────────────┴────────────┘

julia> setdiff(schema(X).names, report(mach).features_to_keep) # dropped features
1-element Vector{Symbol}:
 :comments

```

See also [`OneHotEncoder`](@ref)
