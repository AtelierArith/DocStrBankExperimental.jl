```
DArray(init, dims, [procs, dist])
```

Construct a distributed array.

The parameter `init` is a function that accepts a tuple of index ranges. This function should allocate a local chunk of the distributed array and initialize it for the specified indices.

`dims` is the overall size of the distributed array.

`procs` optionally specifies a vector of process IDs to use. If unspecified, the array is distributed over all worker processes only. Typically, when running in distributed mode, i.e., nprocs() > 1, this would mean that no chunk of the distributed array exists on the process hosting the interactive julia prompt.

`dist` is an integer vector specifying how many chunks the distributed array should be divided into in each dimension.

For example, the `dfill` function that creates a distributed array and fills it with a value `v` is implemented as:

### Example

```jl
dfill(v, args...) = DArray(I->fill(v, map(length,I)), args...)
```
