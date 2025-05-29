```
tess_delete!(
    pipe::TessPipeline,
    wait::Bool = true
)
```

Release all resources associated with the pipeline.

**Arguments:**

| T   | Name | Default | Description                     |
|:--- |:---- |:------- |:------------------------------- |
| R   | pipe |         | The pipeline to release.        |
| O   | wait | `true`  | Wait for the tasks to complete? |

See also: [`TessPipeline`](@ref)
