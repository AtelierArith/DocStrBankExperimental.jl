```
levels(d::UnivariateFinite)
```

`d`を構成するために使用されるクラスの共通プールにおける生のレベルのリストであり、`CategoricalArrays.DataAPI.unwrap.(classes(d))`に等しいです。

```
v = categorical(["yes", "maybe", "no", "yes"])
d = UnivariateFinite(v[1:2], [0.3, 0.7])
levels(d) # Array{String, 1}["maybe", "no", "yes"]
```
