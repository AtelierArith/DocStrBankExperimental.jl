```
power(material::Material)
```

材料に蓄えられたパワーを抽出します。

## 例

```jldoctest
julia> l = Lambertian(τ = 0.1, ρ = 0.2);

julia> power(l);
```
