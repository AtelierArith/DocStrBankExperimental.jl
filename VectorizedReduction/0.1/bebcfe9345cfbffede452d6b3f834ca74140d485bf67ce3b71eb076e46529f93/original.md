```
vtreduce(op, init, A::AbstractArray, dims=:)
```

Reduce `A` over the dimensions `dims` using the binary function `op`. See `vtmapreduce` for description of `op`, `init`, `dims`.

See also: [`vtsum`](@ref), [`vtprod`](@ref), [`vtminimum`](@ref), [`vtmaximum`](@ref)
