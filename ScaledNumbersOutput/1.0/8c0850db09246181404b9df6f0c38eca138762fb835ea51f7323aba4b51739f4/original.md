```
to_SI(x::Real; sigdigits=5)
```

Convert the input number `x` to a string that is rounded by `sigdigits` significant digits and converted to use SI scaling prefixes

# Examples

```jldoctest julia> to_SI(1.5e9) "1.5G"

julia> to_SI(0.00000025) "250n"

julia> to_SI(1/3) "0.33333"

julia> to_SI(1/3, sigdigits=12) "0.333333333333"
