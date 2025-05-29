```
FrameBuffer{T}
```

A buffer for images, this type supports efficient updating and calculation of statistics along it's third dimension.

Construct using     fb = FrameBuffer(img::Matrix, n)     fb = FrameBuffer{T}(w::Int,h::Int,n::Int)

where `n` is the buffer capacity. `fb` supports `push!, median, mean, sum, var, std, reshape, size, length, capacity, Matrix, isready` and iteration.
