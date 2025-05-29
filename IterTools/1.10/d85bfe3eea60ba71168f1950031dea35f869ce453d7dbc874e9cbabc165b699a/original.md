```
repeatedly(f)
repeatedly(f, n)
```

Call function `f` `n` times, or infinitely if `n` is omitted.

```julia
julia> t() = (sleep(0.1); Dates.millisecond(now()))
t (generic function with 1 method)

julia> collect(repeatedly(t, 5))
5-element Vector{Any}:
 993
  97
 200
 303
 408
```
