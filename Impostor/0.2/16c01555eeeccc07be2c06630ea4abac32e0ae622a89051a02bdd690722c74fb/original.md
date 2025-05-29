```
bank_name(n::Integer = 1; kwargs...)
bank_name(options::Vector, n::Integer; level::Symbol, kwargs...)
bank_name(mask::Vector; level::Symbol, kwargs...)
```

# Parameters

  * `n::Integer = 1`: number of bank name entries to generate
  * `options::Vector{<:AbstractString}`: vector with options restricting the possible values generated.
  * `mask::Vector{<:AbstractString}`: mask vector with element-wise option restrictions.

# Kwargs

  * `level::Symbol = :bank_code`: Level of values in `options` or `mask` when using option-based or mask-based eneration.
  * `locale::Vector{String}`: locale(s) from which entries are sampled. If no `locale` is provided, the current session locale is used.

# Example

```@repl
julia> bank_name(5; locale = ["pt_BR"])
5-element Vector{String}:
 "Broker"
 "Nubank"
 "Itaubank"
 "Renascenca"
 "Daycoval"
```
