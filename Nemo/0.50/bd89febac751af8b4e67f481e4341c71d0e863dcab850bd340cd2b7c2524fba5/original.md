```
harmonic(n::Int)
```

Return the harmonic number $H_n = 1 + 1/2 + 1/3 + \cdots + 1/n$. Table lookup is used for $H_n$ whose numerator and denominator fit in a single limb. For larger $n$, a divide and conquer strategy is used.

# Examples

```jldoctest
julia> a = harmonic(12)
86021//27720
```
