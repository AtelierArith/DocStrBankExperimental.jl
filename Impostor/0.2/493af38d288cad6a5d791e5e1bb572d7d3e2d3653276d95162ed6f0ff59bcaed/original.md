```
country_official_name(n::Integer = 1; kws...)
country_official_name(options::Vector{<:AbstractString}, n::Integer; level::Symbol, kws...)
country_official_name(mask::Vector{<:AbstractString}; level::Symbol, kws...)
```

Generate `n` or `length(mask)` country offiical names.

# Parameters

  * `n::Integer = 1`: number of country official names entries to generate.
  * `options::Vector{<:AbstractString}`: vector with with options restricting the possible values generated.
  * `mask::Vector{<:AbstractString}`: mask vector with element-wise option restrictions.

# Kwargs

  * `level::Symbol = :country_code`: Level of values in `options` or `mask` when using option-based or mask-based generation.
  * `locale::Vector{String}`: locale(s) from which entries are sampled. If no `locale` is provided, the current session locale is used.
