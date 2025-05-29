```
×(v::PVector, w::PVector...)
```

Operator version of [`combine`](@ref).

## Example

```julia
julia> v = PVector([1, 2, 3]);
julia> w = PVector([4, 5]);
julia> v × w
[1 : 2 : 3] × [4 : 5]
```
