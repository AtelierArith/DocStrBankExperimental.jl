```
create(c::Client, ::Type{T}, args...; kwargs...) -> Future{Response}
```

作成、追加、送信など。

## 例

[`Message`](@ref)を送信する：

```julia
create(c, Message, channel; content="foo")
```

新しい[`DiscordChannel`](@ref)を作成する：

```julia
create(c, DiscordChannel, guild; name="bar")
```

[`Member`](@ref)を禁止する：

```julia
create(c, Ban, guild, member; reason="baz")
```
