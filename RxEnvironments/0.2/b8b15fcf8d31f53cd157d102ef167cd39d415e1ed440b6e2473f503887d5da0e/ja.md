```
receive!(recipient::AbstractEntity, emitter::AbstractEntity, observation::Any)
```

`emitter` からの観察を受信し、`recipient` の状態をそれに応じて更新します。

関連情報: [`RxEnvironments.send!`](@ref)
