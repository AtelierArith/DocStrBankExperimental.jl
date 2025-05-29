```
@gsl_multiroot_function(f, n)
```

Create a `gsl_multiroot_function` object for a problem of dimension `n`.

`f(x::Array{Float64}, out::Array{Float64})` stores $f(x)$ in `out`
