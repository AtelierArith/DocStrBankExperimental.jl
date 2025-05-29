```
tensor_probability(CG::Array, scenario::Tuple, behaviour::Bool = false)
```

Takes a multipartite Bell functional `CG` in Collins-Gisin notation and transforms it to probability notation. `scenario` is a tuple detailing the number of inputs and outputs, in the order (oa, ob, ..., ia, ib, ...). If `behaviour` is `true` do instead the transformation for behaviours. Doesn't assume normalization.
