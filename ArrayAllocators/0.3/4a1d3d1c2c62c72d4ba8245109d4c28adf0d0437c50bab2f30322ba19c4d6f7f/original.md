```
ArrayAllocators
```

Defines an array allocator interface and concrete array allocators using `malloc`, `calloc`, and memory alignment.

# Examples

```julia
using ArrayAllocators

Array{UInt8}(malloc, 100)
Array{UInt8}(calloc, 1024, 1024)
Array{UInt8}(MemAlign(2^16), (1024, 1024, 16))
```

See also `NumaAllocators`, `SafeByteCalculators`
