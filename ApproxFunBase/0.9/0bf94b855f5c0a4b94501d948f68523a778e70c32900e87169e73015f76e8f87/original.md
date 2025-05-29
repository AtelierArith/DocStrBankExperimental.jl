```
Fun()
```

Return `Fun(identity, Chebyshev())`, which represents the identity function in `-1..1`.

# Examples

```jldoctest
julia> f = Fun(Chebyshev())
Fun(Chebyshev(), [0.0, 1.0])

julia> f(0.1)
0.1
```
