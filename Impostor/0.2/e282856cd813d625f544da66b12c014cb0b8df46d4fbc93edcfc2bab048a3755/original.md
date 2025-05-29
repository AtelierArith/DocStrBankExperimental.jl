```
street(n::Integer = 1; kws...)
street(options::Vector{<:AbstractString}, n::Integer; kws...)
street(mask::Vector{<:AbstractString}; kws...)
```

Generate `n` street names. Note that for option and mask-based generation the only valid options to provide are `country_code`s.

# Parameters

  * `n::Integer = 1`: number of street names entries to generate.
  * `options::Vector{<:AbstractString}`: vector with with options restricting the possible values generated.
  * `mask::Vector{<:AbstractString}`: mask vector with element-wise option restrictions.
