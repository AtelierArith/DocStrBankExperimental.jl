```
Properties()
```

Access all properties of an object. An alias for `Properties()` is available as `∗ₚ` (`\ast\_p`). This optic can also be written as `@o _[∗ₚ]`.

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=2, c=3)
(a = 1, b = 2, c = 3)

julia> set(obj, Properties(), "hi")
(a = "hi", b = "hi", c = "hi")

julia> modify(x -> 2x, obj, Properties())
(a = 2, b = 4, c = 6)
```

Based on [`mapproperties`](@ref).
