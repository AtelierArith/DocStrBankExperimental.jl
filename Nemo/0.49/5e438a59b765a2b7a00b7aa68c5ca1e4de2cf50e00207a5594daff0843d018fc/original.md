```
next_minimal(a::QQFieldElem)
```

Given $a$, return the next rational number in the sequence obtained by enumerating all positive denominators $q$, and for each $q$ enumerating the numerators $1 \le p < q$ in order and generating both $p/q$ and $q/p$, but skipping all gcd$(p,q) \neq 1$. Starting with zero, this generates every non-negative rational number once and only once, with the first few entries being $0, 1, 1/2, 2, 1/3, 3, 2/3, 3/2, 1/4, 4, 3/4, 4/3, \ldots$. This enumeration produces the rational numbers in order of minimal height. It has the disadvantage of being somewhat slower to compute than the Calkin-Wilf enumeration. If $a < 0$ we throw a `DomainError()`.

# Examples

```jldoctest
julia> next_minimal(ZZ(2)//3)
3//2
```
