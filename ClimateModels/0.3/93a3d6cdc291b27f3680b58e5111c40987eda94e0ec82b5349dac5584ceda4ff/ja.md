```
pathof(x::AbstractModelConfig)
```

x の実行ディレクトリパスを返します。すなわち、`joinpath(x.folder,string(x.ID))`
