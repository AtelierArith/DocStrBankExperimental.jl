```
Fun(f, s::Space)
```

Return a `Fun` representing the function, number, or vector `f` in the space `s`.  If `f` is vector-valued, it Return a vector-valued analogue of `s`.

# Examples

```jldoctest
julia> f = Fun(x->x^2, Chebyshev())
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> f(0.1) == (0.1)^2
true
```
