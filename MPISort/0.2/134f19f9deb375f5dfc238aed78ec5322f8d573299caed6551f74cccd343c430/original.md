```
function mpisort!(
    v::AbstractVector;
    alg::SIHSort,
    by=identity,
    kws...
)
```

Distributed MPI-based sorting API with the same inputs as the base Julia sorters.

Important: the input vector will be mutated, but the sorted elements for each MPI rank **will be returned**; this is required as the vector size will change with data migration.

Additional keywords `kws...` are forwarded to the local sorter and `searchsortedlast`.

# Examples

Different sorting settings:

```julia
# Automatically uses MPI.COMM_WORLD as communicator; doesn't save sorting stats
sorted_local_array = mpisort!(local_array; alg=SIHSort())

# Reverse sorting; specify communicator explicitly
sorted_local_array = mpisort!(local_array; alg=SIHSort(comm), rev=true)

# Specify key to sort by; see https://docs.julialang.org/en/v1/base/sort/
sorted_local_array = mpisort!(local_array; alg=SIHSort(), by=x->x["key"])

# Different ordering; see https://docs.julialang.org/en/v1/base/sort/#Alternate-orderings
sorted_local_array = mpisort!(local_array; alg=SIHSort(), order=Reverse)

# Save sorting stats
alg = SIHSort(comm)
sorted_local_array = mpisort!(local_array; alg=alg)

@show alg.stats.splitters               # `nranks - 1` elements splitting arrays between nodes
@show alg.stats.num_elements            # `nranks` integers specifying number of elements on each node

# Use different in-place local sorter
alg = SIHSort(comm, nothing)            # Default: standard Base.sort!
alg = SIHSort(comm, QuickSort)          # Specify algorithm, passed to Base.sort!(...; alg=<Algorithm>)
alg = SIHSort(comm, v -> mysorter!(v))  # Pass any function that sorts a local vector in-place
```
