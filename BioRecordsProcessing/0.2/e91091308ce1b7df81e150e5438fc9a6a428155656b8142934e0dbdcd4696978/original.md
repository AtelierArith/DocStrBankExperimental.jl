```julia
Pipeline(source, processor, sink)
Pipeline(source, sink)
```

Build a Pipeline, if `processor` is omitted it will default to `identity`.
