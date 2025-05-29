```
on_guild_member_add!(
    f::Function
    c::Client
)
```

GUILD*MEMBER*ADDゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
