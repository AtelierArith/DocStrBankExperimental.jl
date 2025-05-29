```
info(registry)
```

レジストリに関する情報を表示します。具体的には、その名前、説明、およびフィールドです。

## 例

{cell}

```julia
using FeatureRegistries: exampleregistry, info
registry = exampleregistry()
info(registry)
```
