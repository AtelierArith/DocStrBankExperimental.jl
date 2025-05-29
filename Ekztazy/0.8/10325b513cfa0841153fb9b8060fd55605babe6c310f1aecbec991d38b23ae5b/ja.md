```
on_guild_role_update!(
    f::Function
    c::Client
)
```

GUILD*ROLE*UPDATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります。

```
    (ctx::Context) -> Any 
```
