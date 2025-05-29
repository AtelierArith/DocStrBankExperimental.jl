```
nationality(n::Integer = 1; kws...)
nationality(options::Vector{<:AbstractString}, n::Integer; level::Symbol, kws...)
nationality(mask::Vector{<:AbstractString}; level::Symbol, kws...)
```

# Parameters

  * `n::Integer = 1`: number of nationality entries to generate.
  * `options::Vector{<:AbstractString}`: vector with options restricting the possible values generated.
  * `mask::Vector{<:AbstractString}`: mask vector with element-wise option restrictions.

# Kwargs

  * `level::Symbol = :district_name`: Level of values in `options` or `mask` when using option-based or mask-based eneration. Valid `level` values are:

      * `:sex`
      * `:country_code`
  * `locale::Vector{String}`: locale(s) from which entries are sampled. If no `locale` is provided, the current session locale is used.
