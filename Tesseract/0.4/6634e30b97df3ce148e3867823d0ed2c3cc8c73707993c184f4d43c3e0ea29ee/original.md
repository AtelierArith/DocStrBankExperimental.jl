```
mutable struct TessPipeline
    inst::TessInst
    ptr::Ptr{Cvoid}
    tasks::Vector{PipelineTask}
    types::Vector{ResultRendererType}
end
```

Allows the client to process multiple images in sequence.

**Values:**

| Name  | Description                                             |
|:----- |:------------------------------------------------------- |
| inst  | The TessInst that will be processing the images.        |
| ptr   | The Tesseract pipeline that will be outputing the data. |
| task  | The list of background tasks associated with pipeline.  |
| types | The list of renderers used in the pipeline.             |

See also: [`tess_run_pipeline`](@ref)
