```
root(x::ZZRingElem, n::Int; check::Bool=true)
```

Return the $n$-the root of $x$. We require $n > 0$ and that $x \geq 0$ if $n$ is even. By default the function tests whether the input was a perfect $n$-th power and if not raises an exception. If `check=false` this check is omitted.

# Examples

```jldoctest
julia> root(ZZ(27), 3; check=true)
3
```
