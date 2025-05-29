```
@gsl_function_fdf(f, df, fdf)
```

Create a `gsl_function_fdf` object.

`f(x::Float64) -> Float64`              Return target functions f 
`df(x::Float64) -> Float64`             Return derivative f' 
`fdf(x::Float64) -> (Float64,Float64)`  Return (f(x), df(x))
