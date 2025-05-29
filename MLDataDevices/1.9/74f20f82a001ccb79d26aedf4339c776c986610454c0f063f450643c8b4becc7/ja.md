```
supported_gpu_backends() -> Tuple{String, ...}
```

サポートされているGPUバックエンドのタプルを返します。

!!! warning
    これはシステム上の機能的バックエンドのリストではなく、むしろ `MLDataDevices.jl` がサポートするバックエンドです。

