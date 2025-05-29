```
CuIterator([to], batches)
```

Create a `CuIterator` that iterates through the provided `batches` via `iterate`. Upon each iteration, the current `batch` is copied to the GPU, and the previous iteration is marked as freeable from GPU memory (via `unsafe_free!`).

The conversion to GPU memory is done recursively, using Adapt.jl, so that each batch can be an array, an array of arrays, or more complex iterable objects. To customize the conversion, an adaptor can be specified as the first argument, e.g., to change the element type:

```julia
julia> first(CuIterator([[1.]]))
1-element CuArray{Float64, 1, CUDA.DeviceMemory}:
 1.0

julia> first(CuIterator(CuArray{Float32}, [[1.]]))
1-element CuArray{Float32, 1, CUDA.DeviceMemory}:
 1.0
```

This abstraction is useful for batching data into GPU memory in a manner that allows old iterations to potentially be freed (or marked as reusable) earlier than they otherwise would via `CuArray`'s internal polling mechanism.
