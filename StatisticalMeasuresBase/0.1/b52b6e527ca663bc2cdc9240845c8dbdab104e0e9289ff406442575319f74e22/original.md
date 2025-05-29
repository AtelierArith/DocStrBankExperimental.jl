```
StatisticalMeasuresBase.multimeasure(atomic_measure; options...)
```

Return a new measure, called a *multi-measure*, which, on a prediction-target pair `(ŷ, y)`, broadcasts `atomic_measure` over `MLUtils.eachobs((ŷ, y))` and aggregates the result. Here `ŷ` and `y` are necessarily objects implementing the MLUtils `getobs/numobs` interface, such as arrays, and tables `X` for which `Tables.istable(X) == true`.

All multi-measures automatically support weights and class weights.

By default, aggregation is performed using the preferred mode for `atomic_measure`, i.e., `StatisticalMeasuresBase.external_aggregation_mode(atomic_measure)`. Internally, aggregation is performed using the [`aggregate`](@ref) method.

Nested applications of `multimeasure` are useful for building measures that apply to matrices and some tables ("multi-targets") as well as multidimensional arrays. See the Advanced Examples below.

# Simple example

```julia
using StatisticalMeasuresBase

# define an atomic measure:
struct L2OnScalars end
(::L2OnScalars)(ŷ, y) = (ŷ - y)^2

julia> StatisticalMeasuresBase.external_aggregation_mode(L2OnScalars())
Mean()

# define a multimeasure:
L2OnVectors() = StatisticalMeasuresBase.multimeasure(L2OnScalars())

y = [1, 2, 3]
ŷ = [7, 6, 5]
@assert L2OnVectors()(ŷ, y) ≈ (ŷ - y).^2 |> mean
```

# Keyword options

  * `mode=StatisticalMeasuresBase.external_aggregation_mode(atomic_measure)`: mode for aggregating the results of broadcasting. Possible values include `Mean()` and `Sum()`. See [`AggregationMode`](@ref) for all options and their meanings. Using `Mean()` in conjunction with weights returns the usual weighted mean scaled by the average weight value. .
  * `transform=identity`: an optional transformation applied to observations in `y` and `ŷ` before passing to each `atomic_measure` call. A useful value is `vec∘collect` which is the identity on vectors, flattens arrays, and converts the observations of some tables (it's "rows") to vectors. See the example below.
  * `atomic_weights=nothing`: the weights to be passed to the atomic measure, on each call to evaluate it on the pair `(transform(ŷᵢ), transform(yᵢ))`, for each `(ŷᵢ, yᵢ)` in `MLUtils.eachjobs(ŷ, y)`. Assumes `atomic_measure` supports weights.
  * `skipnan=false`: whether to skip `NaN` values when aggregating (`missing` values are always skipped)

# Advanced examples

Building on `L2OnVectors` defined above:

```julia
# define measure for multi-dimensional arrays and some tables:
L2() = multimeasure(L2OnVectors(), transform=vec∘collect)

y = rand(3, 5, 100)
ŷ = rand(3, 5, 100)
weights = rand(100)
@assert L2()(ŷ, y, weights) ≈
   sum(vec(mean((ŷ - y).^2, dims=[1, 2])).*weights)/length(weights)

using Tables
y = rand(3, 100)
ŷ = rand(3, 100)
t = Tables.table(y') |> Tables.rowtable
t̂ = Tables.table(ŷ') |> Tables.rowtable
@assert L2()(t̂, t, weights) ≈
   sum(vec(mean((ŷ - y).^2, dims=1)).*weights)/length(weights)
```

!!! note
    The measure traits [`StatisticalMeasuresBase.observation_scitype(measure)`](@ref) (default=`Union{}`) and [`StatisticalMeasuresBase.can_consume_tables(measure)`](@ref) (default=`false`) are not forwarded from the atomic measure and must be explicitly overloaded for measures wrapped using `multimeasure`.

