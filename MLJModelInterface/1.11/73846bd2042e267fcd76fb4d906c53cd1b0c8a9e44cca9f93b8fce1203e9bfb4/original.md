```
decoder(x)
```

Return a callable object for decoding the integer representation of a `CategoricalValue` sharing the same pool the `CategoricalValue` `x`. Specifically, one has `decoder(x)(int(y)) == y` for all `CategoricalValue`s `y` having the same pool as `x`. One can also call `decoder(x)` on integer arrays, in which case `decoder(x)` is broadcast over all elements.

### Examples

```julia-repl
julia> v = categorical(["c", "b", "c", "a"])
4-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "c"
 "b"
 "c"
 "a"

julia> int(v)
4-element Vector{UInt32}:
 0x00000003
 0x00000002
 0x00000003
 0x00000001

julia> d = decoder(v[3]);

julia> d(int(v)) == v
true
```

### Warning:

It is *not* true that `int(d(u)) == u` always holds.

See also: [`int`](@ref).
