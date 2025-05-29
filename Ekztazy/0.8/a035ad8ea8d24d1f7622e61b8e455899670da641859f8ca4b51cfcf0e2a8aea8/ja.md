```
on_guild_ban_remove!(
    f::Function
    c::Client
)
```

GUILD*BAN*REMOVEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
