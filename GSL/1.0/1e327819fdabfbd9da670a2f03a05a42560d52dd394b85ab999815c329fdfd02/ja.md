```
@gsl_multiroot_function_fdf(f, df, n)
```

次元 `n` の問題のために `gsl_multiroot_function_fdf` オブジェクトを作成します。

`f(x::Array{Float64}, out::Array{Float64})` は `out` に $f(x)$ を格納します。

`df(x::Array{Float64}, Jtrans::Array{Float64,2})` は `Jtrans` に $f(x)$ のヤコビ行列の**転置**を格納します。
