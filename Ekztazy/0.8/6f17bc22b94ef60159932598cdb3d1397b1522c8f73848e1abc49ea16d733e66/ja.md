```
@fetch [functions...] ブロック
```

指定されたCRUD関数（[`create`](@ref), [`retrieve`](@ref), [`update`](@ref), および[`delete`](@ref)）へのすべての呼び出しをブロック内で`fetch`でラップします。関数が指定されていない場合、すべてのCRUD関数がラップされます。

## 例

すべてのCRUD関数をラップする：

```julia
@fetch begin
    guild_resp = create(c, Guild; name="foo")
    guild_resp.ok || error("新しいギルドのリクエストに失敗しました")
    channel_resp = retrieve(c, DiscordChannel, guild_resp.val)
end
```

`retrieve`への呼び出しのみをラップする：

```julia
@fetch retrieve begin
    resp = retrieve(c, DiscordChannel, 123)
    future = create(c, Message, resp.val; content="foo")  # 通常通りに動作します。
end
```
