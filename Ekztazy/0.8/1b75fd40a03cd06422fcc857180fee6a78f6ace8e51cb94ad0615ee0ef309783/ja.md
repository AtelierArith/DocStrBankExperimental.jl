```
on_typing_start!(
    f::Function
    c::Client
)
```

TYPING_STARTゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
