Parse complex numbers.

This code doesn't deal with all possible forms of complex numbers, just those output by Mathematica

## Arguments

  * `::Type{Complex{T}}`: the type to parse to, where T is a Real number type
  * `s::AbstractString`: the string to parse

## Examples

```jldoctest; setup = :(using Polylogarithms)
julia> parse( Complex{Float64}, "1.2 - 3.1*I")
1.2 + 3.1im
```
