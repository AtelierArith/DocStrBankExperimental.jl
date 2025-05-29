```
bare_type(x) -> T <: Union{Real,Complex}
```

は、数値または数値型である可能性のある `x` のストレージを支えるベア数値型 `T` を返します。もし `x` に単位がある場合、それらは破棄されます。したがって、`T` は常に単位のない実数または複素数型です。

例:

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

は、`args...` の昇格されたベア数値型を返します。

---

```
bare_type() -> TypeUtils.BareNumber
```

は、引数なしで呼び出されたときに `bare_type` によって返される可能性のあるベア数値型の和を返します。
