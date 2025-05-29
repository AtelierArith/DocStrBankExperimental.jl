```
Fun(s::Space, coefficients::AbstractVector)
```

Return a `Fun` with the specified `coefficients` in the space `s`

# Examples

```jldoctest
julia> f = Fun(Fourier(), [1,1]);

julia> f(0.1) == 1 + sin(0.1)
true

julia> f = Fun(Chebyshev(), [1,1]);

julia> f(0.1) == 1 + 0.1
true
```
