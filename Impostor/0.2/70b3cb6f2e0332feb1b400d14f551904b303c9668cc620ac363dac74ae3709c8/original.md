```
complete_name(n::Integer = 1; kws...)
complete_name(options::Vector{<:AbstractString}, n::Integer; kws...)
complete_name(mask::Vector{<:AbstractString}; kws...)
```

Generate `n` or `length(mask)` full (complete) names from a given locale.

# Parameters

  * `n::Integer = 1`: number of complete names to generate.

# Options

The valid options values for `options` and `mask` are:

  * `"M"` for "male"
  * `"F"` for "female"

# Kwargs

  * `locale::Vector{String}`: locale(s) from which entries are sampled. If no `locale` is provided, the current session locale is used.
  * `max_surnames::Integer = 3`: maximum number of surnames in each of the generated entries, note that the actual number may be smaller than `max_surnames`.

# Examples

```@juliarepl
julia> Impostor.complete_name(["F"], 5)
5-element Vector{String}:
"Melissa Sheffard"
"Kate Collins"
"Melissa Cornell Fraser"
"Abgail Cornell"
"Abgail Fraser Jameson"

julia> complete_name(["F", "M", "F", "F", "M"])
5-element Vector{String}:
"Melissa Sheffard Jameson Cornell"
"Alfred Collins"
"Mary Sheffard Fraser"
"Milly Jameson Fraser"
"Alfred Fraser Collins"
```
