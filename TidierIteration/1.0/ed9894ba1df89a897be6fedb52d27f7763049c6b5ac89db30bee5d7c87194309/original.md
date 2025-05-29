```
map2(d1::Dict, d2::Dict, f)
```

The same as `Dict(k => f(d1[k], d2[k]) for k ∈ keys(d1) ∩ keys(d2))`, that is: we apply `f` on `(d1[k], d2[k])` for every `k` common key between `d1` and `d2`.

# Arguments

  * `d1`: a dictionary.
  * `d2`: a dictionary.
  * `f`: a two-variable function.
