```
@gsl_multiroot_function(f, n)
```

次元 `n` の問題のための `gsl_multiroot_function` オブジェクトを作成します。

`f(x::Array{Float64}, out::Array{Float64})` は `out` に $f(x)$ を格納します。
