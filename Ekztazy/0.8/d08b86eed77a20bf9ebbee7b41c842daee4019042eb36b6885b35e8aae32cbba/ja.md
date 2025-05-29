```
on_guild_member_update!(
    f::Function
    c::Client
)
```

GUILD*MEMBER*UPDATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
