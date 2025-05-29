```
SyntheticFeature(name::String, candidates::Union{UnitRange, AbstractVector})
```

合成特徴生成器で、`candidates` から値をサンプリングすることができます。

```julia
features = SyntheticFeature[]

age = SyntheticFeature("Age", 1930:2010))
push!(features, age)

geo = SyntheticFeature("Geo", ["Arizona", "California", "Colorado", "Illinois", "Indiana", "Michigan", "New York", "Utah"])
push!(features, geo)

rand(geo, 3) # 例: ["California", "New York", "Arizona"]
```
