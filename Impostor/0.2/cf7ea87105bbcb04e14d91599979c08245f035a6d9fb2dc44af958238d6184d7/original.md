```
university(n::Integer = 1; kws...)
university(fields::Vector{<:AbstractString}, n::Integer; kws...)
university(field_mask::Vector{<:AbstractString}; kws...)
```

# Parameters

  * `n::Integer = 1`: number of university entries to generate.
  * `options::Vector{<:AbstractString}`: vector with options restricting the possible values generated.
  * `mask::Vector{<:AbstractString}`: mask vector with element-wise option restrictions.

# Options

The valid options values for elements in `options` and `mask` are:

  * `"business"`
  * `"humanities"`
  * `"social-sciences"`
  * `"natural-sciences"`
  * `"formal-sciences"`
  * `"public-administration"`
  * `"military"`

# Kwargs

  * `locale::Vector{String}`: locale(s) from which entries are sampled. If no `locale` is provided, the current session locale is used.
