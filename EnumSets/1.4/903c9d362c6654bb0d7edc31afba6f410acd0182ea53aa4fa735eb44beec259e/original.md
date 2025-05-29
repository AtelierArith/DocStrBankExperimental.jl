```
enumsettype(::Type{E})::Type
```

Return a subtype of `EnumSet` suitable for storing instances of an enum `E`. Typical usage looks like this:

```julia
@enum Alphabet A B C
const MySet = enumsettype(Alphabet)

ab = MySet((A, B))
bc = MySet((B, C))
ab ∩ bc
...
```
