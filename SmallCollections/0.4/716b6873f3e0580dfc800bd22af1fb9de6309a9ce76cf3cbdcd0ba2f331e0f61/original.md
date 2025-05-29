```
fasthash(v::AbstractFixedVector [, h0::UInt]) -> UInt
```

Return a hash for `v` that may be computed faster than the standard `hash` for vectors. This new hash is consistent across all `AbstractFixedVector`s of the same element type, but it may not be compatible with `hash` or with `fasthash` for a `AbstractFixedVector` having a different element type.

Currently, `fasthash` differs from `hash` only if the element type of `v` is a bit integer type with at most 32 bits, `Bool` or `Char`.

See also `Base.hash`.
