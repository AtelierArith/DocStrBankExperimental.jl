```
SyntheticFeature(name::String, candidates::Union{UnitRange, AbstractVector})
```

Synthetic feature generator that allows us to sample a value from `candidates`.

```julia
features = SyntheticFeature[]

age = SyntheticFeature("Age", 1930:2010))
push!(features, age)

geo = SyntheticFeature("Geo", ["Arizona", "California", "Colorado", "Illinois", "Indiana", "Michigan", "New York", "Utah"])
push!(features, geo)

rand(geo, 3) # e.g., ["California", "New York", "Arizona"]
```
