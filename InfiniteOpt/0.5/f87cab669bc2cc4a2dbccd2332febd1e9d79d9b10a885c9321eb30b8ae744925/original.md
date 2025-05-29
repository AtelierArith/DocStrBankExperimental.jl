```
build_parameter(
    _error::Function, domain::InfiniteScalarDomain;
    [num_supports::Int = 0,
    supports::Union{Real, Vector{<:Real}} = Float64[],
    sig_digits::Int = DefaultSigDigits,
    derivative_method::AbstractDerivativeMethod = DefaultDerivativeMethod]
)::IndependentParameter
```

Returns a [`IndependentParameter`](@ref) given the appropriate information. This is analagous to `JuMP.build_variable`. Errors if supports violate the bounds associated with `domain`. This is meant to primarily serve as a helper method for [`@infinite_parameter`](@ref). Here `derivative_method`  specifies the numerical evalution method that will be applied to derivatives that  are taken with respect to this infinite parameter.

**Example**

```julia-repl
julia> param = build_parameter(error, IntervalDomain(0, 3), supports = Vector(0:3));
```
