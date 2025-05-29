```
on_ready!(
    f::Function
    c::Client
)
```

READYゲートウェイイベントのハンドラーを追加します。`f`パラメータのシグネチャは次のようにする必要があります：

```
    (ctx::Context) -> Any 
```
