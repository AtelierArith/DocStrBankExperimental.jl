```
MaxIter(n)
```

`n` 回の反復の後に学習を停止します。

[`Verbose`](@ref) で `MaxIter` をラップする：

```jldoctest
julia> learn!(nothing, Verbose(MaxIter(5)), 1:100)
INFO: MaxIter: 1/5
INFO: MaxIter: 2/5
INFO: MaxIter: 3/5
INFO: MaxIter: 4/5
INFO: MaxIter: 5/5
INFO: MaxIter(5) finished
```
