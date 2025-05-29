```julia
Pipeline(source, processor, sink)
Pipeline(source, sink)
```

パイプラインを構築します。`processor`が省略された場合、デフォルトで`identity`になります。
