```
rand_poly(T = ComplexF64, vars::AbstractVector{Variable}, d::Integer; homogeneous::Bool = false)
```

与えられた変数 `variables` において次数 `d` のランダムな密な多項式を作成します。各係数は `randn(T)` を介して独立にサンプリングされます。

```julia-repl
julia> @var x y;

julia> rand_poly(Float64, [x, y], 2)
0.788764085756728 - 0.534507647623108*x - 0.778441366874946*y -
 0.128891763280247*x*y + 0.878962738754971*x^2 + 0.550480741774464*y^2
```
