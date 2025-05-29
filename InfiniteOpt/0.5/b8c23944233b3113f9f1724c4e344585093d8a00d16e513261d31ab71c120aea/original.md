```
generate_supports(domain::AbstractInfiniteDomain
                  [method::Type{<:AbstractSupportLabel}];
                  [num_supports::Int = DefaultNumSupports,
                  sig_digits::Int = DefaultSigDigits]
                  )::Tuple{Array{<:Real}, DataType}
```

Generate `num_supports` support values with `sig_digits` significant digits in accordance with `domain` and return them along with the correct generation label(s). `IntervalDomain`s generate supports uniformly with label `UniformGrid` and distribution domains generate them randomly accordingly to the underlying distribution. Moreover, `method` indicates the generation method that should be used. These `methods` correspond to parameter support labels. Current labels that can be used as generation methods include (but may not be defined for certain domain types):

  * [`MCSample`](@ref): Uniformly distributed Monte Carlo samples.
  * [`WeightedSample`](@ref): Monte Carlo samples that are weighted by an underlying PDF.
  * [`UniformGrid`](@ref): Samples that are generated uniformly over the domain.

Extensions that employ user-defined infinite domain types and/or methods should extend [`generate_support_values`](@ref) to enable this. Errors if the `domain` type and /or methods are unrecognized. This is intended as an internal method to be used by methods such as [`generate_and_add_supports!`](@ref).
