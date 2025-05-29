```
static(x)
```

`x`の静的形式を返します。`x`がすでに静的形式である場合は、`x`が返されます。`x`に対する静的な代替がない場合は、エラーがスローされます。

参照: [`is_static`](@ref), [`known`](@ref)

# 例

```julia
julia> using Static

julia> static(1)
static(1)

julia> static(true)
True()

julia> static(:x)
static(:x)

```
