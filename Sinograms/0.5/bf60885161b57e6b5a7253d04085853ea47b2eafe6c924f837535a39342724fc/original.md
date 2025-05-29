```
i = rays(rg::CtGeom)
```

Return parallel-beam coordinates of all rays for this CT geometry. Return type of `i` is a `ProductIterator` that makes tuples of the form `(u, v, ϕ, θ)`. To make projections call `p = [fun(c...) for c in i]` where `fun` is `radon(...)`.
