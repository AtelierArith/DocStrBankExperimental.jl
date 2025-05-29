Return the full stabilizer group represented by the input generating set (a [`Stabilizer`](@ref)).

The returned object is exponentially long.

```jldoctest
julia> groupify(S"XZ ZX")
+ __
+ XZ
+ ZX
+ YY
```
