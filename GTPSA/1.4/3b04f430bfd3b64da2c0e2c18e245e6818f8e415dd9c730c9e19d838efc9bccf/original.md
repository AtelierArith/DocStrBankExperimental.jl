```
setTPS!(t::TPS, t1::Number; change::Bool=false) -> t
```

General function for setting a TPS `t` equal to `t1`. If `change` is `true`, then `t` and `t1` can have different `Descriptor`s (with invalid monomials removed) so  long as the number of variables + number of parameters are equal.
