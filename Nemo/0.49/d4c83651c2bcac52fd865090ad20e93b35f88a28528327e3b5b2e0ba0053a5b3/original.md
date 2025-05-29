```
euler_phi(x::ZZRingElem)
euler_phi(x::Int)
```

Return the value of the Euler phi function at $x$, i.e. the number of positive integers up to $x$ (inclusive) that are coprime with $x$. An exception is raised if $x \leq 0$.

# Examples

```jldoctest
julia> euler_phi(ZZ(12480))
3072

julia> euler_phi(12480)
3072
```
