```
compute(ctx::Context, d::Thunk; options=nothing) -> Chunk
```

Compute a Thunk - creates the DAG, assigns ranks to nodes for tie breaking and runs the scheduler with the specified options. Returns a Chunk which references the result.
