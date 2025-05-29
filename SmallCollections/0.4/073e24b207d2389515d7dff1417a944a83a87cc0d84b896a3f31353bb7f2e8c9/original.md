```
fasthash(s::SmallBitSet [, h0::UInt]) -> UInt
```

Return a hash for `s` that can be computed fast. This hash is consistent across all `SmallBitSet`s, but it is not compatible with the `hash` used for sets.

See also `Base.hash`.

# Examples

```jldoctest
julia> s = SmallBitSet(1:3);

julia> fasthash(s)
0x828a4cc485149963

julia> fasthash(s) == hash(s)
false

julia> t = SmallBitSet{UInt16}(s);

julia> fasthash(s) == fasthash(t)
true
```
