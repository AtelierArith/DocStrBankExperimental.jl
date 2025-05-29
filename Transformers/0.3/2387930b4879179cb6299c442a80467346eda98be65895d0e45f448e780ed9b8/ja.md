```
enable_gpu(t=true)
```

`todevice`のためにGPUを有効にし、`enable_gpu(false)`で無効にします。バックエンドは`Flux.gpu_backend!`によって選択されます。ユーザースクリプトでのみ使用するべきです。
