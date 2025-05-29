```
divergence(f, x)
```

Calculate the divergence of the vector field `f`, in the point `x`.

# Examples

```jldoctest
julia> f(x) = 2x;

julia> x = rand(Vec{3});

julia> divergence(f, x)
6.0
```
