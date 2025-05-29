```
dynamic(x)
```

`x`の「動的」または非静的な形式を返します。`x`が静的型でない場合、変更されずに返されます。

`dynamic`は、コンパイラが正確な値を推論できなくても、返される値の型が常に推論されることを保証します。

参照: [`known`](@ref)

# 例

```julia
julia> dynamic(static(1))
1

julia> dynamic(1)
1

```
