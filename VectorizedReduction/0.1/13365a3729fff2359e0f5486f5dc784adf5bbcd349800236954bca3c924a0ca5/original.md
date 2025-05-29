```
vvmapreduce(f, op, init, A::AbstractArray, dims=:)
```

Apply function `f` to each element of `A`, then reduce the result over the dimensions `dims` using the binary function `op`. The reduction necessitates an initial value `init` which may be `<:Number` or a function which accepts a single type argument (e.g. `zero`); `init` is optional for binary operators `+`, `*`, `min`, and `max`. `dims` may be `::Int`, `::NTuple{M, Int} where {M}` or `::Colon`.

See also: [`vvsum`](@ref), [`vvprod`](@ref), [`vvminimum`](@ref), [`vvmaximum`](@ref)
