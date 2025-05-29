```
on_guild_members_chunk!(
    f::Function
    c::Client
)
```

GUILD*MEMBERS*CHUNKゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
