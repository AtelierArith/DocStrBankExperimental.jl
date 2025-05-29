```
mutable struct TessPipeline
    inst::TessInst
    ptr::Ptr{Cvoid}
    tasks::Vector{PipelineTask}
    types::Vector{ResultRendererType}
end
```

クライアントが複数の画像を順番に処理できるようにします。

**値:**

| 名前    | 説明                          |
|:----- |:--------------------------- |
| inst  | 画像を処理するTessInst。            |
| ptr   | データを出力するTesseractパイプライン。    |
| task  | パイプラインに関連するバックグラウンドタスクのリスト。 |
| types | パイプラインで使用されるレンダラーのリスト。      |

参照: [`tess_run_pipeline`](@ref)
