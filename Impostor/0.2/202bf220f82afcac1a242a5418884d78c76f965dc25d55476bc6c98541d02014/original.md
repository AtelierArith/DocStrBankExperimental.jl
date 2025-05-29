```
prefix(n::Integer = 1; kws...)
prefix(options::Vector{String}, n::Integer; kws...)
prefix(mask::Vector{<:AbstractString}; kws...)
```

Generate `n` name prefixes, *e.g.* `"Mr."` and `"Ms."`, from a given locale.

# Parameters

  * `n::Integer = 1`: number of prefixes to generate.
  * `options::Vector{<:AbstractString}`: vector with options restricting the possible values generated.
  * `mask::Vector{<:AbstractString}`: mask vector with element-wise option restrictions.

# Options

The valid options values for `options` and `mask` are:

  * `"M"` for "male"
  * `"F"` for "female"

# Kwargs

  * `locale::Vector{String}`: locale(s) from which entries are sampled. If no `locale` is provided, the current session locale is used.

# Example

```@juliarepl
julia> prefix(["F", "M", "F"])
3-element Vector{String}:
"Ms."
"Mr."
"Ms."
```
