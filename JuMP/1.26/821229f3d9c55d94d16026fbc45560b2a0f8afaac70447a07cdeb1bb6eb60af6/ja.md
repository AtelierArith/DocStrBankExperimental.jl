```
isequal_canonical(
    x::T,
    y::T
) where {T<:AbstractJuMPScalar,AbstractArray{<:AbstractJuMPScalar}}
```

`x`が`y`と等しい場合は`true`を返します。ゼロを無視し、順序を考慮しません。

このメソッドは主にテストに役立ちます。なぜなら、`x == y`のようなフォールバックは、`x[1] + 0 x[2] + 1 == x[1] + 1`のような有効な数学的比較を考慮しないからです。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> a = x[1] + 1.0
x[1] + 1

julia> b = x[1] + x[2] + 1.0
x[1] + x[2] + 1

julia> add_to_expression!(b, -1.0, x[2])
x[1] + 0 x[2] + 1

julia> a == b
false

julia> isequal_canonical(a, b)
true
```
