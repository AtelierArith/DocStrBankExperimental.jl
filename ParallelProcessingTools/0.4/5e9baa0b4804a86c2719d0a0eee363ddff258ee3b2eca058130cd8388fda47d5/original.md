```
workpart(data::AbstractArray, workersel::AbstractVector{W}, current_worker::W) where {W}
```

Get the part of `data` that the execution unit `current_worker` is responsible for. Implies a partition of `data` across the workers listed in `workersel`.

For generic `data` arrays, `workpart` will return a view. If `data` is a `Range` (e.g. indices to be processed), a sub-range will be returned.

Type `W` will typically be `Int` and `workersel` will usually be a range/array of thread/process IDs.

Note: `workersel` is required to be sorted in ascending order and to contain no duplicate entries.

Examples:

```julia
using Distributed, Base.Threads
A = rand(100)
# ...
sub_A = workpart(A, workers(), myid())
# ...
idxs = workpart(eachindex(sub_A), allthreads(), threadid())
for i in idxs
    # ...
end
```
