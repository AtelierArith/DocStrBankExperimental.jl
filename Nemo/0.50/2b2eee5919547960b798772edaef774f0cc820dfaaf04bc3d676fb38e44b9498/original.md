```
next_calkin_wilf(a::QQFieldElem)
```

Return the next number after $a$ in the breadth-first traversal of the Calkin-Wilf tree. Starting with zero, this generates every non-negative rational number once and only once, with the first few entries being $0, 1, 1/2, 2, 1/3, 3/2, 2/3, 3, 1/4, 4/3, 3/5, 5/2, 2/5, \ldots$. Despite the appearance of the initial entries, the Calkin-Wilf enumeration does not produce the rational numbers in order of height: some small fractions will appear late in the sequence. This order has the advantage of being faster to produce than the minimal-height order.

# Examples

```jldoctest
julia> next_calkin_wilf(ZZ(321)//113)
113//244
```
