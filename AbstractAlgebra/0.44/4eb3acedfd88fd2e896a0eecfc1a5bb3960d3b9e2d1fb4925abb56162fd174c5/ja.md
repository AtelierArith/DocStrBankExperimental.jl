```
laurent_polynomial_ring(R::Ring, s::VarName)
```

基底環 `R` と生成子（変数）の表示方法を指定する文字列 `s` を与えると、新しいローレンツ多項式環 $S = R[x, 1/x]$ と環の生成子 $x$ を表すタプル `S, x` を返します。

# 例

```julia
julia> R, x = laurent_polynomial_ring(ZZ, :x)
(Univariate Laurent Polynomial Ring in x over Integers, x)

julia> 2x^-3 + x^2
x^2 + 2*x^-3

julia> rand(R, -3:3, -9:9)
-3*x^2 - 8*x + 4 + 3*x^-1 - 6*x^-2 + 9*x^-3
```
