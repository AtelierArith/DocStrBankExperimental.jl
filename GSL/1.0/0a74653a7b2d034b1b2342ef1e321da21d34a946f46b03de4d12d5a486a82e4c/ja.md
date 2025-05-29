```
@gsl_multiroot_function_fdf(f, df, fdf, n)
```

次元 `n` の問題のための `gsl_multiroot_function_fdf` オブジェクトを作成します。

`f(x::Array{Float64}, out::Array{Float64})` は `out` に $f(x)$ を格納します。

`df(x::Array{Float64}, Jtrans::Array{Float64,2})` は $f(x)$ のヤコビ行列の**転置**を `Jtrans` に格納します。

`fdf(x::Array{Float64}, out::Array{Float64}), Jtrans::Array{Float64,2})` は上記の両方の操作を行います。
