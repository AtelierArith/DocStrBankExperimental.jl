```
on_guild_integrations_update!(
    f::Function
    c::Client
)
```

GUILD*INTEGRATIONS*UPDATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
