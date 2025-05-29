```
firstname(n::Integer = 1; kws...)
firstname(sexes::Vector{<:AbstractString}, n::Integer; kws...)
firstname(sexes::Vector{<:AbstractString}; kws...))
```

Generate `n` or `length(mask)` first names.

# Parameters

  * `n::Integer = 1`: number of first names to generate.
  * `options::Vector{<:AbstractString}`: vector with options restricting the possible values generated.
  * `mask::Vector{<:AbstractString}`: mask vector with element-wise option restrictions.

# Options

The valid options values for `options` and `mask` are:

  * `"M"` for "male"
  * `"F"` for "female"

# Kwargs

  * `locale::Vector{String}`: locale(s) from which entries are sampled. If no `locale` is provided, the current session locale is used.

# Examples

```@juliarepl
julia> firstname(["F"], 4)
4-element Vector{String}:
"Sophie"
"Abgail"
"Sophie"
"Mary"

julia> firstname(["F", "M", "F", "F", "M"])
5-element Vector{String}:
"Sophie"
"Carl"
"Milly"
"Amanda"
"John"
```
