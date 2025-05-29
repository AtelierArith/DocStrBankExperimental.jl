```
flatten([eltype=Float64], x)
```

Returns a "flattened" representation of `x` as a vector of real numbers, and a function `unflatten` that takes a vector of reals of the same length and returns an object of the same type as `x`.

`unflatten` is the inverse of `flatten`, so

```julia
julia> x = (randn(5), 5.0, (a=5.0, b=randn(2, 3)));

julia> v, unflatten = flatten(x);

julia> x == unflatten(v)
true
```
