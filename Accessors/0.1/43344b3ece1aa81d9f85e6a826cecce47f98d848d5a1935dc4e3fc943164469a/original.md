```
Elements
```

Access all elements of a collection that implements `map`. An alias for `Elements()` is available as `∗` (`\ast`). This optic can also be written as `@o _[∗]`.

```jldoctest
julia> using Accessors

julia> obj = (1,2,3);

julia> set(obj, Elements(), 0)
(0, 0, 0)

julia> modify(x -> 2x, obj, Elements())
(2, 4, 6)
```
