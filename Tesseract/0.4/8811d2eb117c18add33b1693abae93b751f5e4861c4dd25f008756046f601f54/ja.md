```
tess_delete!(
    pipe::TessPipeline,
    wait::Bool = true
)
```

パイプラインに関連付けられたすべてのリソースを解放します。

**引数:**

| T   | 名前   | デフォルト  | 説明            |
|:--- |:---- |:------ |:------------- |
| R   | pipe |        | 解放するパイプライン。   |
| O   | wait | `true` | タスクの完了を待ちますか？ |

関連情報: [`TessPipeline`](@ref)
