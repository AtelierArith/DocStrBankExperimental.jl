```
witharray(f, v::CeedVector, mtype=MEM_HOST)
```

Calls `f` with an array containing the data of the `CeedVector` `v`, using [`memory type`](@ref MemType) `mtype`.

Because of performance issues involving closures, if `f` is a complex operation, it may be more efficient to use the macro version `@witharray` (cf. the section on "Performance of captured variable" in the [Julia documentation](https://docs.julialang.org/en/v1/manual/performance-tips) and related [GitHub issue](https://github.com/JuliaLang/julia/issues/15276).

# Examples

Return the sum of a vector:

```
witharray(sum, v)
```
