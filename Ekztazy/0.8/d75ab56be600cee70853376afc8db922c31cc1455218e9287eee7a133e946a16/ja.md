```
on_presence_update!(
    f::Function
    c::Client
)
```

PRESENCE_UPDATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
