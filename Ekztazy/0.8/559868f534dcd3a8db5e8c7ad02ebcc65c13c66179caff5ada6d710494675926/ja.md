```
on_guild_role_delete!(
    f::Function
    c::Client
)
```

GUILD*ROLE*DELETEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
