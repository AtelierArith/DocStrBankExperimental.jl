```
real_type(x) -> T <: Real
```

yields the bare numeric type `T` backing the storage of `x` which may be a number of a numeric type. If `x` is a complex, `T` is the bare numeric type of the real and imaginary parts of `x`. If `x` has units, they are discarded. Hence `T` is always a unitless real type.

Examples:

```jldoctest
julia> using TypeUtils

julia> map(real_type, (-3.14f0, 1 + 0im, Complex{Int8}))
(Float32, Int64, Int8)

julia> using Unitful

julia> real_type(u"3km/s")
Int64
```

---

```
real_type(args...)
```

yields the promoted bare real type of `args...`.

---

```
real_type() -> Real
```

yields the supertype of the types that may be returned by `real_type` when called with no arguments.
