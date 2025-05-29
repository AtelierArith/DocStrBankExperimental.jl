```
solve(problem, property; usecuda=false, T=Float64)
```

Solving a certain property of a graph problem.

## Positional Arguments

  * `problem` is the graph problem with tensor network information,
  * `property` is string specifying the task. Using the maximum independent set problem as an example, it can be one of

      * [`PartitionFunction`](@ref)`()` for computing the partition function,
      * [`SizeMax`](@ref)`(k=Single)` for finding maximum-$k$ set sizes,
      * [`SizeMin`](@ref)`(k=Single)` for finding minimum-$k$ set sizes,
      * [`CountingMax`](@ref)`(k=Single)` for counting configurations with maximum-$k$ sizes,
      * [`CountingMin`](@ref)`(k=Single)` for counting configurations with minimum-$k$ sizes,
      * [`CountingAll`](@ref)`()` for counting all configurations,
      * [`PartitionFunction`](@ref)`()` for counting all configurations,
      * [`GraphPolynomial`](@ref)`(; method=:finitefield, kwargs...)` for evaluating the graph polynomial,
      * [`SingleConfigMax`](@ref)`(k=Single; bounded=false)` for finding one maximum-$k$ configuration for each size,
      * [`SingleConfigMin`](@ref)`(k=Single; bounded=false)` for finding one minimum-$k$ configuration for each size,
      * [`ConfigsMax`](@ref)`(k=Single; bounded=true, tree_storage=false)` for enumerating configurations with maximum-$k$ sizes,
      * [`ConfigsMin`](@ref)`(k=Single; bounded=true, tree_storage=false)` for enumerating configurations with minimum-$k$ sizes,
      * [`ConfigsAll`](@ref)`(; tree_storage=false)` for enumerating all configurations,

## Keyword arguments

  * `usecuda` is a switch to use CUDA (if possible), user need to call statement `using CUDA` before turning on this switch.
  * `T` is the "base" element type, sometimes can be used to reduce the memory cost.
