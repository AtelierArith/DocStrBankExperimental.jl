```
de2bi(d::Integer; width::Int = 0)::Vector{Int}
```

Convert a decimal number to a binary vector.

# Arguments

  * `d::Integer`: The decimal number to convert
  * `width::Int = 0`: The desired width of the output vector. If 0, the minimum required width is used.

# Returns

  * `Vector{Int}`: A vector of 0s and 1s representing the binary form of the input number

# Examples

```julia
julia> de2bi(5)
3-element Vector{Int64}:
 1
 0
 1

julia> de2bi(5, width=4)
4-element Vector{Int64}:
 1
 0
 1
 0
```
