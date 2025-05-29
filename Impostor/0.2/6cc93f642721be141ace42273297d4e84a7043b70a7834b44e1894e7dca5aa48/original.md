```
address(n::Integer = 1; kws...)
address(options::Vector{<:AbstractString}, n::Integer = 1; level::Symbol, kws...)
address(mask::Vector{<:AbstractString}; level::Symbol, kws...)
```

Generate `n` or `length(mask)` addresses based on `options` or `mask` according to the required `level`. For example, let `level = :country_code` and `options` be the required country codes to generate addresses for, *e.g.* `["BRA", "USA"]`, the expected output will contain only addresses (in their specific formats) for location in Brazil (`"BRA"`) and the United States (`"USA"`). Other values may be passed as `level`.

# Parameters

  * `n::Integer = 1`: number of addresses to generate.
  * `options::Vector{<:AbstractString}`: vector with options restricting the possible values generated.
  * `mask::Vector{<:AbstractString}`: mask vector with element-wise option restrictions.

# Kwargs

  * `level::Symbol = :state_code`: option level to be used when using option and mask-based generation.
