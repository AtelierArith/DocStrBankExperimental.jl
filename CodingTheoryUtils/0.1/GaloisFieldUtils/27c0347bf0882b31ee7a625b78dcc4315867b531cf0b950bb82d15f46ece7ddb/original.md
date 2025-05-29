```
de2f2(d::Integer; width::Int = 0)::Vector{F2}
```

Convert a decimal number to a vector of F2 elements.

# Arguments

  * `d::Integer`: The decimal number to convert
  * `width::Int = 0`: The desired width of the output vector. If 0, the minimum required width is used.

# Returns

  * `Vector{F2}`: A vector of F2 elements representing the binary form of the input number

# Examples

```julia
julia> de2f2(5)
3-element Vector{F2}:
 1
 0
 1

julia> de2f2(5, width=4)
4-element Vector{F2}:
 1
 0
 1
 0
```
