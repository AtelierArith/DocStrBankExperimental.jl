```
zz2vector(n) -> ZZ2Vector
```

Return a `ZZ2Vector` containing the bit representation of `n`. Here `n` must be a `Base.BitInteger` or a bit integer defined by the package `BitIntegers.jl`.

See also [`zz2vector!`](@ref), `Base.BitInteger`, `BitIntegers.AbstractBitSigned`, `BitIntegers.AbstractBitUnsigned`.

# Example

```jldoctest
julia> zz2vector(Int8(35))
8-element ZZ2Vector:
 1
 1
 0
 0
 0
 1
 0
 0
```
