```
on_voice_state_update!(
    f::Function
    c::Client
)
```

VOICE*STATE*UPDATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
