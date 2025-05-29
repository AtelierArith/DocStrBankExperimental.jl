```
credit_card_number(n::Integer = 1; kwargs...)
credit_card_number(options::Vector{<:AbstractString}, n::Integer; kwargs...)
credit_card_number(mask::Vector{<:AbstractString}; kwargs...)
```

Generate valid credit card numbers according to the credit card vendor. Available vendors are:

  * `"Visa"`
  * `"American Express"`
  * `"MasterCard"`

# Parameters

  * `n::Integer = 1`: number of credit card numbers to generate.
  * `options::Vector{<:AbstractString}`: vector with options restricting the possible values generated.
  * `mask::Vector{<:AbstractString}`: mask vector with element-wise option restrictions.

# Kwargs

  * `formatted::Bool`: whether to return the raw credit card numbers *e.g.* `"3756808757861311"` or to format the output *e.g.* `"3756-8087-5786-1311"`

# Examples

```@repl
julia> credit_card_number()
"5186794250685172"

julia> credit_card_number(; formatted = true)
"4046-7508-2101-2729"
```
