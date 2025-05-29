```
zz2vector!(a::ZZ2Vector, n) -> a
```

Fill `a` with the bit representation of `n` and return `a`. Here `n` must be a `Base.BitInteger` or a bit integer defined by the package `BitIntegers.jl`. The length of `a` is set to the bit length of `n`.

See also [`zz2vector`](@ref), `Base.BitInteger`, `BitIntegers.AbstractBitSigned`, `BitIntegers.AbstractBitUnsigned`.
