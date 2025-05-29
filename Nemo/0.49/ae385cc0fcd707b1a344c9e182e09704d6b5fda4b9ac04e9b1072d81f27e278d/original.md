```
number_of_digits(x::ZZRingElem, b::Integer)
```

Return the number of digits of $x$ in the base $b$ (default is $b = 10$).

# Examples

```jldoctest
julia> number_of_digits(ZZ(12), 3)
3
```
