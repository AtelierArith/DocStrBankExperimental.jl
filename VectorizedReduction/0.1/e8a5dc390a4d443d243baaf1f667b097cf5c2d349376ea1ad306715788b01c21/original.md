```
vvreduce(op, init, A::AbstractArray, dims=:)
```

Reduce `A` over the dimensions `dims` using the binary function `op`. See `vvmapreduce` for description of `op`, `init`, `dims`.

See also: [`vvsum`](@ref), [`vvprod`](@ref), [`vvminimum`](@ref), [`vvmaximum`](@ref)
