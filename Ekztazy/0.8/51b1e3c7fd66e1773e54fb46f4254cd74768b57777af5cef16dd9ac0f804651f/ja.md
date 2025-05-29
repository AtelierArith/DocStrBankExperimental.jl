```
@deferred_fetch [functions...] ブロック
```

[`@fetch`](@ref) と同じですが、`Future` はブロックの**終わり**まで `fetch` されません。これはより効率的ですが、ブロック内にデータ依存関係がない場合にのみ機能します。

## 例

これは動作します：

```julia
@deferred_fetch begin
    guild_resp = create(c, Guild; name="foo")
    channel_resp = retrieve(c, DiscordChannel, 123)
end
```

これは動作しません。なぜなら、2回目の呼び出しが最初の値に依存しているからです：

```julia
@deferred_fetch begin
    guild_resp = create(c, Guild; name="foo")
    channels_resp = retrieve(c, DiscordChannel, guild_resp.val)
end
```
