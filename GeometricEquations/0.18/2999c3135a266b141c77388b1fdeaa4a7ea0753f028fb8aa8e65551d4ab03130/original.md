`GeometricEquation{invType,parType,perType}` is the abstract type all equation types are derived from.

All equations should have fields for defining invariants, parameters and periodicity of the main state variable. The types of these fields are stored in the following type parameters:

  * `invType <: OptionalInvariants`: invariants type
  * `parType <: OptionalParameters`: parameters type
  * `perType <: OptionalPeriodicity`: periodicity type

The `Optional*` types are all unions of the respective `Null*` types and `NamedTuple` or `AbstractArray`, i.e.,

```julia
const OptionalInvariants = Union{NamedTuple, NullInvariants}
const OptionalParameters = Union{NamedTuple, NullParameters}
const OptionalPeriodicity = Union{AbstractArray, NullPeriodicity}
```

The `Null*` types are empty structs, merely used for dispatch and the traits `hasinvariants`, `hasparameters` and `hasperiodicity`.
