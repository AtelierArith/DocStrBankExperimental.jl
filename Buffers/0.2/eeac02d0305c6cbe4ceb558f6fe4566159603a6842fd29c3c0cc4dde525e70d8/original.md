```
Buffers module
```

This module contains functions to handle buffers.

The [`Buffer`](@ref) object is used to store data of type `T` with an offset, while the [`ThreadsBuffer`](@ref) object is used to store data of type `T` with an offset for each thread.

The buffers are used to store data in a contiguous memory block and to avoid memory allocation in loops. The buffers can be used with [`alloc!`](@ref) to allocate tensors of given dimensions, [`drop!`](@ref) to drop tensors from the buffer, and [`reset!`](@ref) to reset the buffer to the initial state.

Alternativelly, the buffers can be reshaped with [`reshape_buf!`](@ref) to use the same memory block for different tensors or to allocate tensors with a specific offset.

The size of the buffer can be extended if necessary, and the buffer can be set to be extendable (default) or not at construction with [`Buffer`](@ref) or later with [`set_extendable!`](@ref).

In any case, the `::ThreadsBuffer` buffers should be released after use with [`Buffers.release!`](@ref) or [`reset!`](@ref).

If some functions complain about tensors being aliases or if the tensors will be used in C,  the [`neuralyze`](@ref) function can be used to wipe the memory about the origin of the tensor. Do not use this function if the size of the tensor might be changed in between, i.e., neuralyze the tensor only after all necessary allocations are done.
