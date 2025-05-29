```
Measure(m)
```

Convert a measure-like object `m` to a measure in the sense of StatisticalMeasuresBase.jl; see [`StatisticalMeasuresBase.is_measure`](@ref) for the definition.

Typically, `Measure` is applied to measures with pre-existing calling behaviour different from that specified by StatisticalMeasuresBase.jl.

# New implementations

To make a measure-like object of type `M` wrappable by `Measure`, implement the appropriate methods below. The first and last are compulsory.

```
(m::Measure{M})(ŷ, y)
(m::Measure{M})(ŷ, y, weights)
(m::Measure{M})(ŷ, y, class_weights::AbstractDict)
(m::Measure{M}, ŷ, y, weights, class_weights)
StatisticalMeasuresBase.measurements(m::Measure{M}, ŷ, y)
StatisticalMeasuresBase.measurements(m::Measure{M}, ŷ, y, weights)
StatisticalMeasuresBase.measurements(m::Measure{M}, ŷ, y, class_weights::AbstractDict)
StatisticalMeasuresBase.measurements(m::Measure{M}, ŷ, y, weights, class_weights)
StatisticalMeasuresBase.is_measure(m::Measure{M}) where M = true
```

In your implementations, you may use [`StatisticalMeasuresBase.unwrap`](@ref) to access the unwrapped object, i.e., `StatisticalMeasuresBase.unwrap(Measure(m)) === m`.

# Sample implementation

To wrap the `abs` function as a measure that computes the absolute value of differences:

```
import StatisticalMeasuresBase as API

(measure::API.Measure{typeof(abs)})(yhat, y) = API.unwrap(measure)(yhat - y)
API.is_measure(::API.Measure{typeof(abs)}) = true

julia> API.Measure(abs)(2, 5)
3
```
