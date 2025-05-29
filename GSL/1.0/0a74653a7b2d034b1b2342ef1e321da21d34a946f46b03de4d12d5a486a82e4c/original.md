```
@gsl_multiroot_function_fdf(f, df, fdf, n)
```

Create a `gsl_multiroot_function_fdf` object for a problem of dimension `n`.

`f(x::Array{Float64}, out::Array{Float64})` stores $f(x)$ in `out`.

`df(x::Array{Float64}, Jtrans::Array{Float64,2})` stores the **TRANSPOSE** of the Jacobian of $f(x)$ in `Jtrans`.

`fdf(x::Array{Float64}, out::Array{Float64}), Jtrans::Array{Float64,2})` does both of the above operations.
