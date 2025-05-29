```
de2f2poly(d::Integer; width::Int = 0)::Polynomial{F2,:x}
```

Convert a decimal number to a polynomial over F2.

# Arguments

  * `d::Integer`: The decimal number to convert
  * `width::Int = 0`: The desired width of the polynomial coefficients. If 0, the minimum required width is used.

# Returns

  * `Polynomial{F2,:x}`: A polynomial over F2 representing the binary form of the input number

# Examples

```julia
julia> de2f2poly(5)
Polynomial(1 + x^2)

julia> de2f2poly(5, width=4)
Polynomial(1 + x^2)
```
