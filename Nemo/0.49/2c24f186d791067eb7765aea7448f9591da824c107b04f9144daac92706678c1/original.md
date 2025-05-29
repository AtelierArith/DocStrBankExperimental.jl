```
next_signed_calkin_wilf(a::QQFieldElem)
```

Given a signed rational number $a$ returns the next element in the Calkin-Wilf sequence with negative numbers interleaved. The sequence begins $0, 1, -1, 1/2, -1/2, 2, -2, 1/3, -1/3, \ldots$. Starting with zero, this generates every rational number once and only once, but not in order of minimal height.

# Examples

```jldoctest
julia> next_signed_calkin_wilf(-ZZ(51)//(17))
1//4
```
