```
bi2de(b::Vector{<:Integer})::Int
```

Convert a binary vector to a decimal number.

# Arguments

  * `b::Vector{<:Integer}`: A vector of 0s and 1s representing a binary number

# Returns

  * `Int`: The decimal representation of the input binary vector

# Examples

```julia
julia> bi2de([1, 0, 1])
5

julia> bi2de([0, 1, 0, 1])
10
```
