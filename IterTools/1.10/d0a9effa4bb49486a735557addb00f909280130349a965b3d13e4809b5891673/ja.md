```
takewhile(cond, xs)
```

条件 `cond` が真である限り、イテレータ `xs` から値を生成するイテレータです。

```jldoctest
julia> collect(takewhile(x-> x^2 < 10, 1:100))
3-element Vector{Int64}:
 1
 2
 3
```
