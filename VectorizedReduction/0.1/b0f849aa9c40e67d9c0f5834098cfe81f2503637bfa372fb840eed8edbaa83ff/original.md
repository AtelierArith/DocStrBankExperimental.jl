```
vtmapreduce(f, op, init, A::AbstractArray, dims=:)
```

Apply function `f` to each element of `A`, then reduce the result over the dimensions `dims` using the binary function `op`. Threaded. See `vvmapreduce` for description of `dims`. `init` need not be provided when `op` is one of `+`, `*`, `min`, `max`.

See also: [`vtsum`](@ref), [`vtprod`](@ref), [`vtminimum`](@ref), [`vtmaximum`](@ref)
