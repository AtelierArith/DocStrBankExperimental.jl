```
gpu_backend!() = gpu_backend!("")
gpu_backend!(backend) = gpu_backend!(string(backend))
gpu_backend!(backend::AbstractGPUDevice)
gpu_backend!(backend::String)
```

指定されたGPUバックエンドを持つ`LocalPreferences.toml`ファイルを作成します。

`backend == ""`の場合、`gpu_backend`の設定は削除されます。それ以外の場合、`backend`は可能なバックエンドの1つであることが検証され、設定は`backend`に設定されます。

新しいバックエンドが正常に設定された場合、変更を反映させるためにJuliaセッションを再起動する必要があります。
