```
on_guild_ban_add!(
    f::Function
    c::Client
)
```

GUILD*BAN*ADDゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
