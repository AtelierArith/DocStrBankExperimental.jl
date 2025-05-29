```
jacobiweight(a,b, d::AbstractInterval)
```

The [`JacobiWeight`](@ref) affine-mapped to interval `d`.

# Examples

```jldoctest
julia> J = jacobiweight(1, 1, 0..1)
(1-x)^1 * (1+x)^1 on -1..1 affine mapped to 0 .. 1

julia> axes(J)
(Inclusion(0 .. 1),)

julia> J[0.5]
1.0
```
