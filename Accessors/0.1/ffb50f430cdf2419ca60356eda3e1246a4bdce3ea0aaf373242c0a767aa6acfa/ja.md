```
Properties()
```

オブジェクトのすべてのプロパティにアクセスします。`Properties()`のエイリアスは`∗ₚ`（`\ast\_p`）として利用可能です。このオプティックは`@o _[∗ₚ]`としても書くことができます。

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=2, c=3)
(a = 1, b = 2, c = 3)

julia> set(obj, Properties(), "hi")
(a = "hi", b = "hi", c = "hi")

julia> modify(x -> 2x, obj, Properties())
(a = 2, b = 4, c = 6)
```

[`mapproperties`](@ref)に基づいています。
