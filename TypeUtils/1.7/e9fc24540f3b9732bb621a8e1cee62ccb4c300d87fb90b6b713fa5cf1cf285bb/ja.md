```
to_same_type(x1, x2, ...) -> xp1, xp2, ...
```

は、インスタンス `x1`, `x2`, ... を同じ型に変換します。このメソッドは、変換された値が同じ型であることを保証しない `promote(x1,x2,...)` の代わりに使用できます。

例:

```julia
julia> using Unitful, TypeUtils

julia> promote(2, 3.0)
(2.0, 3.0)

julia> to_same_type(2, 3.0)
(2.0, 3.0)

julia> promote(2u"mm", 3.0)
(2.0 mm, 3.0)

julia> to_same_type(2u"mm", 3.0)
ERROR: ArgumentError: types `Quantity{Int64, 𝐋, Unitful.FreeUnits{(mm,), 𝐋, nothing}}` and `Float64` cannot be converted to a common concrete type
Stacktrace:
 ...

julia> promote(2u"mm", 4.0u"nm")
(0.002 m, 4.0e-9 m)

julia> to_same_type(2u"mm", 4.0u"nm")
(0.002 m, 4.0e-9 m)
```

また、[`to_same_concrete_type`](@ref) も参照してください。
