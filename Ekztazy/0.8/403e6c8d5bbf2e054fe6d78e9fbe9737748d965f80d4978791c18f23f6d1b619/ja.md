```
on_guild_emojis_update!(
    f::Function
    c::Client
)
```

GUILD*EMOJIS*UPDATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
