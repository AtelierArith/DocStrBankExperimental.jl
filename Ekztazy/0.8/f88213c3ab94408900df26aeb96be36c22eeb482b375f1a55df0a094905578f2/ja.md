```
update(c::Client, x::T, args...; kwargs...) -> Future{Response}
```

更新、編集、修正など。

## 例

[`Message`](@ref)の編集:

```julia
update(c, message; content="foo2")
```

[`Webhook`](@ref)の修正:

```julia
update(c, webhook; name="bar2")
```

[`Role`](@ref)の更新:

```julia
update(c, role, guild; permissions=8)
```
