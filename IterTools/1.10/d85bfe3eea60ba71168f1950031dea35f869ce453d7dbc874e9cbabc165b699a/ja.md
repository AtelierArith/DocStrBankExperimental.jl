```
repeatedly(f)
repeatedly(f, n)
```

関数 `f` を `n` 回呼び出します。`n` が省略された場合は無限に呼び出します。

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
