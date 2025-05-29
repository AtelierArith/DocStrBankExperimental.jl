```
solve_elastostatic(Q::NTuple{N,Polynomial{N,T}};μ=1,ν=1)
```

ベクトルの多項式 `U` を計算します。これは `μ/(1-2ν) ∇(div U) + μΔU = Q` を満たします。`Q` は同次である必要があります。

# 例

```jldoctest
julia> Q = (Polynomial((1,2)=>1), Polynomial((0,0)=>1))
(xy², 1)

julia> P = solve_elastostatic(Q;ν=1//2)
(-1//8xy + 1//480x⁵ + 1//32x³y² + 1//24xy⁴, 3//16x² + 1//16y² - 1//120y⁵ - 1//96x⁴y - 1//32x²y³)
```
