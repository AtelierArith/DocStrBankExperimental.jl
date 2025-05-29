```
on_guild_member_remove!(
    f::Function
    c::Client
)
```

GUILD*MEMBER*REMOVEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
