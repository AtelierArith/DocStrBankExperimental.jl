```
on_guild_create!(
    f::Function
    c::Client
)
```

GUILD_CREATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
