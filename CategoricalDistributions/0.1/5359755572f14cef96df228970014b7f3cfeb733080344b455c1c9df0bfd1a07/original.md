```
levels(d::UnivariateFinite)
```

A list of the raw levels in the common pool of classes used to construct `d`, equal to `CategoricalArrays.DataAPI.unwrap.(classes(d))`.

```
v = categorical(["yes", "maybe", "no", "yes"])
d = UnivariateFinite(v[1:2], [0.3, 0.7])
levels(d) # Array{String, 1}["maybe", "no", "yes"]
```
