```
is_prime(x::ZZRingElem)
is_prime(x::Int)
```

Return `true` if $x$ is a prime number, otherwise return `false`.

# Examples

```jldoctest
julia> is_prime(ZZ(13))
true
```
