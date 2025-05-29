```
div_diff(f, x::AbstractVector; kwargs...)
div_diff(f, x::Tuple; kwargs...)
div_diff(f, x...; kwargs...)
```

分割差分 `f[x_0,x_1,...,x_n]` を返します。ここで、`f` は `f(x)` として呼び出されると仮定します。可能なキーワード引数の説明については `mat_fun` を参照してください。
