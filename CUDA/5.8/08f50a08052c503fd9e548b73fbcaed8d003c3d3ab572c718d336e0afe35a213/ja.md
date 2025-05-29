```
stream!(::CuStream)
stream!(::CuStream) do ... end
```

現在実行中のタスクのデフォルトCUDAストリームを変更します。doブロックバージョンを使用している場合は、一時的に変更されます。
