```
context()::CuContext
```

現在のスレッドのためのCUDAコンテキストを取得または作成します（現在のスレッドにバウンドされたコンテキストがない場合、`current_context`は`nothing`を返す可能性があります）。
