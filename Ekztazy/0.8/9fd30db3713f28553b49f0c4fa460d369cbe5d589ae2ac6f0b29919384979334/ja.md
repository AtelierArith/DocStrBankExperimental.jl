```
delete(c::Client, x::T, args...) -> Future{Response}
```

削除、取り除く、破棄する、など。

## 例

[`Member`](@ref)をキックする:

```julia
delete(c, member)
```

[`Member`](@ref)のアンバンをする:

```julia
delete(c, ban, guild)
```

[`Message`](@ref)からすべての[`Reaction`](@ref)を削除する（注：これは型パラメータを取る唯一の更新/削除メソッドです）:

```julia
delete(c, Reaction, message)
```
