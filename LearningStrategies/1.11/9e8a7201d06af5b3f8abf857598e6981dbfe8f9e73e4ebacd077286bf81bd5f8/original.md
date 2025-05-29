```
MaxIter(n)
```

Stop learning after `n` iterations.

Wrapping `MaxIter` with [`Verbose`](@ref):

```jldoctest
julia> learn!(nothing, Verbose(MaxIter(5)), 1:100)
INFO: MaxIter: 1/5
INFO: MaxIter: 2/5
INFO: MaxIter: 3/5
INFO: MaxIter: 4/5
INFO: MaxIter: 5/5
INFO: MaxIter(5) finished
```
