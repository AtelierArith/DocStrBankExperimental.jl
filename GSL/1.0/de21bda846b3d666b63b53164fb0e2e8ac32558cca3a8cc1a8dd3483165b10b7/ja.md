```
@gsl_function_fdf(f, df, fdf)
```

`f(x::Float64) -> Float64`              目標関数 f を返します  `df(x::Float64) -> Float64`             導関数 f' を返します  `fdf(x::Float64) -> (Float64,Float64)`  (f(x), df(x)) を返します
