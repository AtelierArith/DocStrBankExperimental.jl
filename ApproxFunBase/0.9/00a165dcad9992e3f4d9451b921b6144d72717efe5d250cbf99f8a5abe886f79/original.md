```
Fun(s::Space)
```

Return `Fun(identity, s)`

# Examples

```jldoctest
julia> x = Fun(Chebyshev())
Fun(Chebyshev(), [0.0, 1.0])

julia> x(0.1)
0.1
```
