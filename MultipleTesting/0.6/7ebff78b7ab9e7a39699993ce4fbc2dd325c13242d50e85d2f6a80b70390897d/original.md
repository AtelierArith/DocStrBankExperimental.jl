Wilkinson's p-value combination

# Examples

```jldoctest
julia> pv = PValues([0.01, 0.02, 0.3, 0.5]);

julia> combine(pv, Wilkinson(1))  # combination with rank 1
0.03940399000000003

julia> combine(pv, Wilkinson(4))  # combination with rank 4
0.0625
```

# References

Wilkinson, B. (1951). A statistical consideration in psychological research. Psychological Bulletin 48, 156.
