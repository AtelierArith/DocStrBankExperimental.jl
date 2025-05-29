```
sum_mutating!(accumulator, [f! = add!], iterator)
```

Add the sum of elements in `iterator` to `accumulator`, storing the result in `accumulator`. If `f!` is provided, it must accept two arguments, the first being the accumulator and the second the element of the iterator. Otherwise, `add!` is used.

See also [`mapreduce`](@ref).
