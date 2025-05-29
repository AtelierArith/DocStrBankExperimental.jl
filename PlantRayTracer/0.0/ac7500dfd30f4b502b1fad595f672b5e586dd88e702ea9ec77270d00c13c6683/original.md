```
reset!(material::Material)
```

Reset the power stored inside a material back to zero

## Examples

```jldoctest
julia> l = Lambertian(τ = 0.1, ρ = 0.2);

julia> l.power[1] = 10.0;

julia> reset!(l);

julia> l;
```
