```
real_type(x) -> T <: Real
```

は、数値型の数である可能性がある `x` のストレージを支える素の数値型 `T` を返します。もし `x` が複素数であれば、`T` は `x` の実部と虚部の素の数値型です。もし `x` に単位がある場合、それらは破棄されます。したがって、`T` は常に単位のない実数型です。

例:

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

は、`args...` の昇格された素の実数型を返します。

---

```
real_type() -> Real
```

は、引数なしで `real_type` を呼び出したときに返される可能性のある型のスーパタイプを返します。
