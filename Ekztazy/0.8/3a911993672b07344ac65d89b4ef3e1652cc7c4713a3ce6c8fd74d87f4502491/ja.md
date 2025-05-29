```
on_guild_delete!(
    f::Function
    c::Client
)
```

GUILD_DELETEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
