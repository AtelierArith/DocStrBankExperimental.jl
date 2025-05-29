```
build_parameter(_error::Function, value::Real)::FiniteParameter
```

Returns a [`FiniteParameter`](@ref) given the appropriate information. This is analagous to `JuMP.build_variable`. This is meant to primarily serve as a helper method for [`@finite_parameter`](@ref).

**Example**

```jldoctest; setup = :(using InfiniteOpt)
julia> build_finite_parameter(error, 1)
FiniteParameter(1.0)
```
