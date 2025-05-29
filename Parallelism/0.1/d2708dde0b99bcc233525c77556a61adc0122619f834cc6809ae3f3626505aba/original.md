```
tmap(f, xs...; basesize=1)
```

Multithreaded version of `map`. `basesize` controls the minimum number of items from `xs` to process per `@spawn`ed task.

!!! tip
    `basesize` should be set high enough that proccessing that many items takes about ~1ms. This is to counter the ~50μs overhead it takes to dispatch work to a thread. If the function takes >1ms per call, then `basesize=1` is recommended.

