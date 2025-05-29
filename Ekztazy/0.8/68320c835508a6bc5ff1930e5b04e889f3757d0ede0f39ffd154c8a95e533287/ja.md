```
retrieve(c::Client, ::Type{T}, args...; kwargs...) -> Future{Response{T}}
```

取得、取得、リストなど。

## 例

[`Client`](@ref)の[`User`](@ref)を取得する:

```julia
retrieve(c, User)
```

[`Guild`](@ref)の[`DiscordChannel`](@ref)を取得する:

```julia
retrieve(c, DiscordChannel, guild)
```

コードによる[`Guild`](@ref)への[`Invite`](@ref)を取得する:

```julia
retrieve(c, Invite, "abcdef")
```
