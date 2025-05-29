```
reset!(material::Material)
```

材料内に蓄えられた電力をゼロにリセットします

## 例

```jldoctest
julia> l = Lambertian(τ = 0.1, ρ = 0.2);

julia> l.power[1] = 10.0;

julia> reset!(l);

julia> l;
```
