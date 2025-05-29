```
nonneg(mat::Material{U,V}, elm::Element)::U where {U<:AbstractFloat,V<:AbstractFloat}
nonneg(mat::Material{UncertainValue,V}, elm::Element)::Float64 where {V<:AbstractFloat}
nonneg(mat::Material)::Material
```

`elm::Element`の質量分率を非負に切り捨てて返します。負の値は0.0として返されます。正の値はそのまま返されます。
