```
taylor_coeff(f, x[, n]; rationalize=true, kwargs...)
```

`f`のテイラー級数の`n`-次係数を`x = 0`の周りで計算します。`rationalize`が`true`の場合、浮動小数点係数は有理数として近似されます（これは、例えば無理数に対して予期しない結果を生じる可能性があります）。キーワード引数`kwargs...`は内部の`substitute()`呼び出しに転送されます。

# 例

```jldoctest
julia> @variables x y
2-element Vector{Num}:
 x
 y

julia> taylor_coeff(series(y, x, 0:5), x, 0:2:4)
3-element Vector{Num}:
 y[0]
 y[2]
 y[4]
```
