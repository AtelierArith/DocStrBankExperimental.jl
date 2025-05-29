```
bounded(val::Array{<:Real}, lower_bound::Real, upper_bound::Real)
```

Roughly equivalent to `bounded.(val, lower_bound, upper_bound)`, but implemented such that unflattening can be efficiently differentiated through using algorithmic differentiation (Zygote in particular).
