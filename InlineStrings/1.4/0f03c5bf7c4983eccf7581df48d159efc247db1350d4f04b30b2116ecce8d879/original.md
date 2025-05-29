```
inlinestrings(itr) => Vector

Utility function that takes any iterator of `AbstractString` values
```

and attempts to produce a `Vector` with a single promoted `InlineString` type. That is, all iterated elements will be promoted to the smallest `InlineString` subtype that can fit all elements. If any value is larger than the current largest InlineString type (256 bytes), the entire collection will be promoted to `String` instead. `missing` values are also allowed and will result in a result eltype of `Union{Missing, X}` where `X` is an `InlineString` subtype or `String`.
