```
combine(v::PVector, w::PVector...)
```

Combine the projective vectors `v` and `wᵢ` to the flattened product. There is also an operator version, [`×`](@ref) (written `imes<tab>`).

## Example

```julia
julia> v = PVector([1, 2, 3]);
julia> w = PVector([4, 5]);
julia> combine(v, w)
[1 : 2 : 3] × [4 : 5]
```
