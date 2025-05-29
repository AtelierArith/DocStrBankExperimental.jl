```
Worker
```

A worker that performs tasks asynchronously.

# Constructor

```
Worker{T}(; [setup], [teardown]) where {T}
```

Constructs a new `Worker` object.

## Arguments

  * `setup`: A function to be executed before the worker starts processing tasks. (optional)
  * `teardown`: A function to be executed after the worker finishes processing tasks. (optional)
