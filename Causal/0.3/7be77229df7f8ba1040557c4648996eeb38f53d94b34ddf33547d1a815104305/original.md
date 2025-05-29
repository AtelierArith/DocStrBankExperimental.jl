```julia
struct Cyclic <: Causal.CyclicMode
```

Cyclic buffer mode. The data is written to buffer until the buffer is full. When the buffer is full, new data is written by overwriting the data available in the buffer starting from the beginning of the buffer. When the buffer is read, the element written last is returned and the returned element is not deleted from the buffer.
