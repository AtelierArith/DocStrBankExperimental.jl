```
bare_type(x) -> T <: Union{Real,Complex}
```

yields the bare numeric type `T` backing the storage of `x` which may be a number or a numeric type. If `x` has units, they are discarded. Hence `T` is always a unitless real or complex type.

Examples:

```jldoctest
julia> map(bare_type, (1, 3.14f0, π, 1 + 0im))
(Int64, Float32, Irrational{:π}, Complex{Int64})

julia> using Unitful

julia> map(bare_type, (u"3km/s", u"3.2km/s", typeof(u"2.1GHz")))
(Int64, Float64, Float64)
```

---

```
bare_type(args...) -> T <: Union{Real,Complex}
```

yields the promoted bare numeric type of `args...`.

---

```
bare_type() -> TypeUtils.BareNumber
```

yields the union of bare numeric types that may be returned by `bare_type` when called with no arguments.
