```
UnivariateFillImputer
```

A model type for constructing a single variable fill imputer, based on [MLJModels.jl](https://github.com/JuliaAI/MLJModels.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
UnivariateFillImputer = @load UnivariateFillImputer pkg=MLJModels
```

Do `model = UnivariateFillImputer()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `UnivariateFillImputer(continuous_fill=...)`.

Use this model to imputing `missing` values in a vector with a fixed value learned from the non-missing values of training vector.

For imputing missing values in tabular data, use [`FillImputer`](@ref) instead.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, x)
```

where

  * `x`: any abstract vector with element scitype `Union{Missing, T}` where `T` is a subtype of `Continuous`, `Multiclass`, `OrderedFactor` or `Count`; check scitype using `scitype(x)`

Train the machine using `fit!(mach, rows=...)`.

# Hyper-parameters

  * `continuous_fill`: function or other callable to determine value to be imputed in the case of `Continuous` (abstract float) data; default is to apply `median` after skipping `missing` values
  * `count_fill`: function or other callable to determine value to be imputed in the case of `Count` (integer) data; default is to apply rounded `median` after skipping `missing` values
  * `finite_fill`: function or other callable to determine value to be imputed in the case of `Multiclass` or `OrderedFactor` data (categorical vectors); default is to apply `mode` after skipping `missing` values

# Operations

  * `transform(mach, xnew)`: return `xnew` with missing values imputed with the fill values learned when fitting `mach`

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `filler`: the fill value to be imputed in all new data

# Examples

```
using MLJ
imputer = UnivariateFillImputer()

x_continuous = [1.0, 2.0, missing, 3.0]
x_multiclass = coerce(["y", "n", "y", missing, "y"], Multiclass)
x_count = [1, 1, 1, 2, missing, 3, 3]

mach = machine(imputer, x_continuous)
fit!(mach)

julia> fitted_params(mach)
(filler = 2.0,)

julia> transform(mach, [missing, missing, 101.0])
3-element Vector{Float64}:
 2.0
 2.0
 101.0

mach2 = machine(imputer, x_multiclass) |> fit!

julia> transform(mach2, x_multiclass)
5-element CategoricalArray{String,1,UInt32}:
 "y"
 "n"
 "y"
 "y"
 "y"

mach3 = machine(imputer, x_count) |> fit!

julia> transform(mach3, [missing, missing, 5])
3-element Vector{Int64}:
 2
 2
 5
```

For imputing tabular data, use [`FillImputer`](@ref).
