```
synchronize([stream::CuStream])
```

`stream` の実行が完了するまで待機します。`stream` は現在の Julia タスクに関連付けられたストリームがデフォルトとなります。

関連情報: [`device_synchronize`](@ref)
