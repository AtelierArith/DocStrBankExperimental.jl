```
on_resumed!(
    f::Function
    c::Client
)
```

RESUMEDゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
