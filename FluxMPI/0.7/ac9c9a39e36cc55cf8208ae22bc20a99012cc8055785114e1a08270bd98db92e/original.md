```
allreduce_gradients(gs::NamedTuple; on_gpu::Bool=CUDA.functional())
```

Allreduce the gradients. This uses a non-blocking API which will be efficient for large containers of multiple parameter arrays.

## Arguments

  * `gs`: A `NamedTuple` of gradients

## Keyword Arguments

  * `on_gpu`: Specify if the gradients are on GPU. Defaults to `CUDA.functional()`

## Returns

  * `Allreduce`d NamedTuple of gradients
