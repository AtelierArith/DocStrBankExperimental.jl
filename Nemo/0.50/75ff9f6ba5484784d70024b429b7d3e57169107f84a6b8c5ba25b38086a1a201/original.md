```
isqrtrem(x::ZZRingElem)
```

Return a tuple $s, r$ consisting of the floor $s$ of the square root of $x$ and the remainder $r$, i.e. such that $x = s^2 + r$. We require $x \geq 0$.

# Examples

```jldoctest
julia> isqrtrem(ZZ(13))
(3, 4)

```
