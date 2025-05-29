```
on_voice_server_update!(
    f::Function
    c::Client
)
```

VOICE*SERVER*UPDATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
