```
trainrun(train::Train, path::Path, settings::Settings)
```

`train` の `path` 上での走行時間を計算します。`settings` は計算のためのモデルの選択を提供します。`settings` は省略可能です。その場合、デフォルトが使用されます。走行時間は秒単位で返されます。

# 例

```julia-repl
julia> trainrun(train, path)[end,:t]
xxx.xx # 秒単位
```
