```
mod(a::QQFieldElem, b::ZZRingElem)
mod(a::QQFieldElem, b::Integer)
```

Return $a \pmod{b}$ where $b$ is an integer coprime to the denominator of $a$.

# Examples

```jldoctest
julia> mod(-ZZ(2)//3, 7)
4

julia> mod(ZZ(1)//2, ZZ(5))
3
```
