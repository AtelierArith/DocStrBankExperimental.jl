`scalar(p::Mvp)`

If `p` is a scalar, return that scalar, otherwise return `nothing`.

```julia-repl
julia> p=Mvp(:x)+1
Mvp{Int64}: x+1

julia> w=p(x=4)
Mvp{Int64}: 5

julia> scalar(w)
5

julia> typeof(scalar(w))
Int64
```

if  `p` is an array, then apply `scalar` to its elements and return `nothing` if it contains any `Mvp` which is not a scalar.
