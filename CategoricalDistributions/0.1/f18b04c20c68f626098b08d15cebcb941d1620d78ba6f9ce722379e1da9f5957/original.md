```
Distributions.pdf(d::UnivariateFinite, x)
```

Probability of `d` at `x`.

```
v = categorical(["yes", "maybe", "no", "yes"])
d = UnivariateFinite(v[1:2], [0.3, 0.7])
pdf(d, "yes")     # 0.3
pdf(d, v[1])      # 0.3
pdf(d, "no")      # 0.0
pdf(d, "house")   # throws error
```

Other similar methods are available too:

```
mode(d)    # CategoricalValue{String, UInt32} "maybe"
rand(d, 5) # CategoricalArray{String,1,UInt32}["maybe", "no", "maybe", "maybe", "no"] or similar
d = fit(UnivariateFinite, v)
pdf(d, "maybe") # 0.25
logpdf(d, "maybe") # log(0.25)
```

One can also do weighted fits:

```
w = [1, 4, 5, 1] # some weights
d = fit(UnivariateFinite, v, w)
pdf(d, "maybe") ≈ 4/11 # true
```

See also `classes`, `support`.
