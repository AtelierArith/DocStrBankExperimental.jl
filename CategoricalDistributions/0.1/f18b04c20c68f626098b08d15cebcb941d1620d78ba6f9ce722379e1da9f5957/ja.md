```
Distributions.pdf(d::UnivariateFinite, x)
```

`d`の`x`における確率。

```
v = categorical(["yes", "maybe", "no", "yes"])
d = UnivariateFinite(v[1:2], [0.3, 0.7])
pdf(d, "yes")     # 0.3
pdf(d, v[1])      # 0.3
pdf(d, "no")      # 0.0
pdf(d, "house")   # エラーをスロー
```

他にも似たようなメソッドがあります：

```
mode(d)    # CategoricalValue{String, UInt32} "maybe"
rand(d, 5) # CategoricalArray{String,1,UInt32}["maybe", "no", "maybe", "maybe", "no"] または類似
d = fit(UnivariateFinite, v)
pdf(d, "maybe") # 0.25
logpdf(d, "maybe") # log(0.25)
```

重み付きフィッティングも行えます：

```
w = [1, 4, 5, 1] # 一部の重み
d = fit(UnivariateFinite, v, w)
pdf(d, "maybe") ≈ 4/11 # 真
```

`classes`、`support`も参照してください。
