```
Distributions.support(d::UnivariateFinite)
Distributions.support(d::UnivariateFiniteArray)
```

非ゼロ確率に関連するクラスの順序付きリスト。

```
v = categorical(["yes", "maybe", "no", "yes"])
d = UnivariateFinite(v[1:2], [0.3, 0.7])
Distributions.support(d) # CategoricalArray{String,1,UInt32}["maybe", "yes"]
```
