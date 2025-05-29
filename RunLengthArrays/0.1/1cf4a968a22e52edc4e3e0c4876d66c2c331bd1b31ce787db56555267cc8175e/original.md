An array of objects of type `T` encoded using run-length compression.

This works like an array, but it is designed to be extremely efficient when the array is long and consists of long repetitions («runs») of the same elements. The length of each run is held using type `N`; this type should be chosen according to the expected maximum length of a run.

Once a `RunLengthArray` has been created, new elements can be added only at the end of it, using `push!` (add one element) or `append!` (add a sequence of elements).

```julia
arr = RunLengthArray{Int, Int8}(Int8[3, 3, 3, 7, 7, 7, 7, 7, 7, 4])

longarr = collect(arr)

@assert length(arr) == 10
@assert sum(arr) == 30
@assert arr[1] == 3
@assert arr[2] == 3

println("$(sizeof(arr))")  # Prints 16 (bytes)
println("$(sizeof(longarr))")  # Prints 56 (bytes)
```
