```
power(material::Material)
```

Extract the power stored inside a material.

## Examples

```jldoctest
julia> l = Lambertian(τ = 0.1, ρ = 0.2);

julia> power(l);
```
