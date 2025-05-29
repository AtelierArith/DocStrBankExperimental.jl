```
Tracer{T}(::Type{T}, f, b=1)
```

Store `f(model, i)` every `b` iterations.

To extract the data `Tracer` collected, `collect(tracer)`. Note that this operation will copy.

```jldoctest
julia> t = Tracer(Int, (model, i) -> @show(i))
Tracer(1, #5, 0-element Array{Int64,1})

julia> learn!(nothing, strategy(MaxIter(3), t))
i = 1
i = 2
i = 3

julia> collect(t)
3-element Array{Int64,1}:
 1
 2
 3
```
