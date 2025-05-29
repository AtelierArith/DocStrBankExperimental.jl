```
solve_stokes(Q::NTuple{N,Polynomial{N,T}};μ=1)
```

ベクトルの多項式 `U` と多項式 `P` を計算し、`μΔU - ∇P = Q` を満たし、`∇ ⋅ U = 0` となるようにします。`Q` は同次である必要があります。

# 例

```jldoctest
julia> Q = (Polynomial((1,0)=>1),Polynomial((0,0)=>1))
(x, 1)

julia> P = solve_stokes(Q;μ=Rational(1))
((-1//8xy + 1//16xy² + 1//48x³, 3//16x² + 1//16y² - 1//48y³ - 1//16x²y), -1//2y - 3//8x² - 1//8y²)
```
