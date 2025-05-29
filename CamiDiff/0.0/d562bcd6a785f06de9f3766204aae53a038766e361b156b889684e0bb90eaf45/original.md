```
regularize!(f::Vector{T} [; k=3]) where T<:Real
```

Regularization of a function with a non-analytic point in the origin.

#### Example:

```
julia> r = [0,1,2,3,4,5];

julia> f = r ./ r; println(f)
[NaN, 1.0, 1.0, 1.0, 1.0, 1.0]

julia> regularize!(f); ; println(f)
[1.0, 1.0, 1.0, 1.0, 1.0, 1.0]
```
