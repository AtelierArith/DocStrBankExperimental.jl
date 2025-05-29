```
Standardizer
```

A model type for constructing a standardizer, based on [MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
Standardizer = @load Standardizer pkg=MLJModels
```

Do `model = Standardizer()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `Standardizer(features=...)`.

Use this model to standardize (whiten) a `Continuous` vector, or relevant columns of a table. The rescalings applied by this transformer to new data are always those learned during the training phase, which are generally different from what would actually standardize the new data.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X)
```

where

  * `X`: any Tables.jl compatible table or any abstract vector with `Continuous` element scitype (any abstract float vector). Only features in a table with `Continuous` scitype can be standardized; check column scitypes with `schema(X)`.

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `features`: one of the following, with the behavior indicated below:

      * `[]` (empty, the default): standardize all features (columns) having `Continuous` element scitype
      * non-empty vector of feature names (symbols): standardize only the `Continuous` features in the vector (if `ignore=false`) or `Continuous` features *not* named in the vector (`ignore=true`).
      * function or other callable: standardize a feature if the callable returns `true` on its name. For example, `Standardizer(features = name -> name in [:x1, :x3], ignore = true, count=true)` has the same effect as `Standardizer(features = [:x1, :x3], ignore = true, count=true)`, namely to standardize all `Continuous` and `Count` features, with the exception of `:x1` and `:x3`.

    Note this behavior is further modified if the `ordered_factor` or `count` flags are set to `true`; see below
  * `ignore=false`: whether to ignore or standardize specified `features`, as explained above
  * `ordered_factor=false`: if `true`, standardize any `OrderedFactor` feature wherever a `Continuous` feature would be standardized, as described above
  * `count=false`: if `true`, standardize any `Count` feature wherever a `Continuous` feature would be standardized, as described above

# Operations

  * `transform(mach, Xnew)`: return `Xnew` with relevant features standardized according to the rescalings learned during fitting of `mach`.
  * `inverse_transform(mach, Z)`: apply the inverse transformation to `Z`, so that `inverse_transform(mach, transform(mach, Xnew))` is approximately the same as `Xnew`; unavailable if `ordered_factor` or `count` flags were set to `true`.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `features_fit` - the names of features that will be standardized
  * `means` - the corresponding untransformed mean values
  * `stds` - the corresponding untransformed standard deviations

# Report

The fields of `report(mach)` are:

  * `features_fit`: the names of features that will be standardized

# Examples

```
using MLJ

X = (ordinal1 = [1, 2, 3],
     ordinal2 = coerce([:x, :y, :x], OrderedFactor),
     ordinal3 = [10.0, 20.0, 30.0],
     ordinal4 = [-20.0, -30.0, -40.0],
     nominal = coerce(["Your father", "he", "is"], Multiclass));

julia> schema(X)
┌──────────┬──────────────────┐
│ names    │ scitypes         │
├──────────┼──────────────────┤
│ ordinal1 │ Count            │
│ ordinal2 │ OrderedFactor{2} │
│ ordinal3 │ Continuous       │
│ ordinal4 │ Continuous       │
│ nominal  │ Multiclass{3}    │
└──────────┴──────────────────┘

stand1 = Standardizer();

julia> transform(fit!(machine(stand1, X)), X)
(ordinal1 = [1, 2, 3],
 ordinal2 = CategoricalValue{Symbol,UInt32}[:x, :y, :x],
 ordinal3 = [-1.0, 0.0, 1.0],
 ordinal4 = [1.0, 0.0, -1.0],
 nominal = CategoricalValue{String,UInt32}["Your father", "he", "is"],)

stand2 = Standardizer(features=[:ordinal3, ], ignore=true, count=true);

julia> transform(fit!(machine(stand2, X)), X)
(ordinal1 = [-1.0, 0.0, 1.0],
 ordinal2 = CategoricalValue{Symbol,UInt32}[:x, :y, :x],
 ordinal3 = [10.0, 20.0, 30.0],
 ordinal4 = [1.0, 0.0, -1.0],
 nominal = CategoricalValue{String,UInt32}["Your father", "he", "is"],)
```

See also [`OneHotEncoder`](@ref), [`ContinuousEncoder`](@ref).
