```
leaf_setter(x::Tuple)
leaf_setter(x::NamedTuple)
leaf_setter(::Type)
```

Return a function for constructing values with the same schema as `x`, given values for the leaves.

EXAMPLE:

```
julia> x = randnt(2,2)
(b = (b = :b, n = :n), k = (h = :h, t = :t))

julia> f = leaf_setter(x)
function = (##265, ##266, ##267, ##268;) -> begin
    begin
        (b = (b = var"##265", n = var"##266"), k = (h = var"##267", t = var"##268"))
    end
end

julia> @btime ($f)(1,2,3,4)
  0.010 ns (0 allocations: 0 bytes)
(b = (b = 1, n = 2), k = (h = 3, t = 4))
```
