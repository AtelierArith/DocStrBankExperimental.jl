```
signedsquare(x)
```

Return `sign(x)*x*x = x*abs(x)`. If `x` is a `RationalRoot`, return an appropriate rational type.

```jldoctest
julia> signedsquare(-2)
-4

julia> signedsquare(4.0)
16.0

julia> signedsquare(-RationalRoot{Int}(3//2))
-9//4
```
