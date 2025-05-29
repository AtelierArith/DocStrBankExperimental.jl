```
(xg, yg, ...) = ndgrid(M, N, ...)
```

`ndgrid(1:M, 1:N, ...)` の省略形です。

# 例

```jldoctest
julia> ndgrid(2,3)
([1 1 1; 2 2 2], [1 2 3; 1 2 3])
```
