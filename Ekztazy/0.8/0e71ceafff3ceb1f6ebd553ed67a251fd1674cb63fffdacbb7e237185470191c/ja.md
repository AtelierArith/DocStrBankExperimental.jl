```
on_guild_role_create!(
    f::Function
    c::Client
)
```

GUILD*ROLE*CREATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
