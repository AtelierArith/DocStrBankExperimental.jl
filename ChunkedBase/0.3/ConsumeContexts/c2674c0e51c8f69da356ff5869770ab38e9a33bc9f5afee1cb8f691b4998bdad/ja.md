```
task_done!(consume_ctx::AbstractConsumeContext, chunking_ctx::ChunkingContext)
```

残りの作業単位の期待数を1つ減らします。各 `consume!` 呼び出しの後に呼び出されます。

この関数は、対応する `setup_tasks!` 呼び出しから得られる `ntasks` 回呼び出されるべきです。

[`consume!`](@ref)、[`setup_tasks!`](@ref)、[`cleanup`](@ref) も参照してください。
