```
sum_mutating!(accumulator, [f! = add!], keys(::PDVec); [init])
sum_mutating!(accumulator, [f! = add!], values(::PDVec); [init])
sum_mutating!(accumulator, [f! = add!], pairs(::PDVec); [init])
```

Perform a parallel sum on [`PDVec`](@ref)s for vector-valued results while minimizing allocations. The result of the sum will be added to `accumulator` and stored in `accumulator`. MPI-compatible. If `f!` is provided, it must accept two arguments, the first being the accumulator and the second the element of the iterator. Otherwise,`add!` is used.

If provided, `init` must be a neutral element for `+` and of the same type as `accumulator`.

See also [`mapreduce`](@ref).
