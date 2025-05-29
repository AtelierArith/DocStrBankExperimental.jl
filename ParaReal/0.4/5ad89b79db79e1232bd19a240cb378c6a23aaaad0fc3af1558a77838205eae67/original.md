```
is_pipeline_failed(pl::Pipeline) -> Bool
```

Determine whether some stage of a pipeline has exited because an exception was thrown. Does not block and not throw an error, if the pipeline failed.
