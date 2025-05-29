```
Distributions.support(d::UnivariateFinite)
Distributions.support(d::UnivariateFiniteArray)
```

Ordered list of classes associated with non-zero probabilities.

```
v = categorical(["yes", "maybe", "no", "yes"])
d = UnivariateFinite(v[1:2], [0.3, 0.7])
Distributions.support(d) # CategoricalArray{String,1,UInt32}["maybe", "yes"]
```
