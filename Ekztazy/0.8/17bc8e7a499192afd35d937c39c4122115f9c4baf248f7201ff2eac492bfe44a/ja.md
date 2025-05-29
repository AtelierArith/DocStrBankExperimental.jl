```
on_channel_pins_update!(
    f::Function
    c::Client
)
```

CHANNEL*PINS*UPDATEゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
