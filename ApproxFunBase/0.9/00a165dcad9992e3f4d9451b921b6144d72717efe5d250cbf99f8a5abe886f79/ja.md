```
Fun(s::Space)
```

`Fun(identity, s)`

# 例

```jldoctest
julia> x = Fun(Chebyshev())
Fun(Chebyshev(), [0.0, 1.0])

julia> x(0.1)
0.1
```
