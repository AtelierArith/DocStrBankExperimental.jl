```
measures(; trait_options...)
```

*Experimental* and subject to breaking behavior between patch releases.

Return a dictionary, `dict`, keyed on measure constructors provided by StatisticalMeasures.jl. The value of `dict[constructor]` provides information about traits (measure "metadata") shared by all measures constructed using the syntax `constructor(args...)`.

# Trait options

One can filter on the basis of measure trait values, as shown in this example:

```
using StatisticalMeasures
import ScientificTypesBase.Multiclass

julia> measures(
    observation_scitype = Union{Missing,Multiclass},
    supports_class_weights = true,
)
```

---

```
measures(y; trait_filters...)
measures(yhat, y; trait_filters...)
```

*Experimental* and subject to breaking behavior between patch releases.

Assuming, ScientificTypes.jl has been imported, find measures that can be applied to data with the specified data arguments `(y,)` or `(yhat, y)`. It is assumed that the arguments contain multiple observations (have types implementing `MLUtils.getobs`).

Returns a dictionary keyed on the constructors of such measures. Additional `trait_filters` are the same as for the zero argument `measures` method.

```julia
using StatisticalArrays
using ScientificTypes

julia> measures(rand(3), rand(3), supports_weights=false)
LittleDict{Any, Any, Vector{Any}, Vector{Any}} with 1 entry:
  RSquared => (aliases = ("rsq", "rsquared"), consumes_multiple_observations = true, can_re…
```

*Warning.* Matching is based only on the *first* observation of the arguments provided, and must be interpreted carefully if, for example, `y` or `yhat` are vectors with `Union` or other abstract element types.
