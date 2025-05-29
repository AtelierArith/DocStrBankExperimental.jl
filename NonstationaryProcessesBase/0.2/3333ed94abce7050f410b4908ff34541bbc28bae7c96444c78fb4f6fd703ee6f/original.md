```
tuplef2ftuple(f::Tuple{Function}, params::Tuple)
```

Convert a vector of curried functions `f` that each accept an element of the parameter tuple `params` into a function of the form `f(t) -> x::Vector`, where `xᵢ = fᵢ(paramsᵢ)(t)` for `i = 1:length(f)`
