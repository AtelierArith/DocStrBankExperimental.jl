```
bank_official_name(n::Integer = 1; kwargs...)
bank_official_name(options::Vector, n::Integer; level::Symbol, kwargs...)
bank_official_name(mask::Vector; level::Symbol, kwargs...)
```

# Parameters

  * `n::Integer = 1`: number of official bank name entries to generate
  * `options::Vector{<:AbstractString}`: vector with options restricting the possible values generated.
  * `mask::Vector{<:AbstractString}`: mask vector with element-wise option restrictions.

# Kwargs

  * `level::Symbol = :bank_code`: Level of values in `options` or `mask` when using option-based or mask-based eneration.
  * `locale::Vector{String}`: locale(s) from which entries are sampled. If no `locale` is provided, the current session locale is used.
