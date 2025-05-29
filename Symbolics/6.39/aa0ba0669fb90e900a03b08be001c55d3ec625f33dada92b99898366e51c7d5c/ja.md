```
taylor(f, x, [x0=0,] n; rationalize=true, kwargs...)
```

`f`のテイラー級数の`n`-次の項を`x = x0`の周りで計算します。`rationalize`が`true`の場合、浮動小数点係数は有理数として近似されます（これは、例えば無理数に対して予期しない結果を生じる可能性があります）。キーワード引数`kwargs...`は内部の`substitute()`呼び出しに転送されます。

# 例

```jldoctest
julia> @variables x
1-element Vector{Num}:
 x

julia> taylor(exp(x), x, 0:3)
1 + x + (1//2)*(x^2) + (1//6)*(x^3)

julia> taylor(exp(x), x, 0:3; rationalize=false)
1.0 + x + 0.5(x^2) + 0.16666666666666666(x^3)

julia> taylor(√(x), x, 1, 0:3)
1 + (1//2)*(-1 + x) - (1//8)*((-1 + x)^2) + (1//16)*((-1 + x)^3)

julia> isequal(taylor(exp(im*x), x, 0:5), taylor(exp(im*x), x, 0:5))
true
```
