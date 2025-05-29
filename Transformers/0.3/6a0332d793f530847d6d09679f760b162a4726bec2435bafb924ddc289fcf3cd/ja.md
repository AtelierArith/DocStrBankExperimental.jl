```
todevice(x)
```

データをデバイスに移動します。`enable_gpu`が有効な場合のみ、基本的には`Flux.gpu`と等しいです。それ以外の場合は単に`Flux.cpu`です。
