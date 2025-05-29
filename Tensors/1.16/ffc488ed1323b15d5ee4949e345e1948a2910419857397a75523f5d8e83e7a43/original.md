```
laplace(f, x)
```

Calculate the laplacian of the field `f`, in the point `x`. If `f` is a vector field, use broadcasting.

# Examples

```jldoctest
julia> x = rand(Vec{3});

julia> f(x) = norm(x);

julia> laplace(f, x)
2.9633756571179273

julia> g(x) = x*norm(x);

julia> laplace.(g, x)
3-element Vec{3, Float64}:
 1.9319830062026155
 3.2540895437409754
 1.2955087437219237
```
