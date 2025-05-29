```
iroot(x::ZZRingElem, n::Int)
```

Return the integer truncation of the $n$-the root of $x$ (round towards zero). We require $n > 0$ and that $x \geq 0$ if $n$ is even.

# Examples

```jldoctest
julia> iroot(ZZ(13), 3)
2
```
