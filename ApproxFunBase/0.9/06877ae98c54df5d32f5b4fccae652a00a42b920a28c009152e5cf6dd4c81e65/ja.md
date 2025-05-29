```
Derivative(sp::Space, k::AbstractVector{Int})
```

多変数空間における部分微分演算子を返します。例えば、

```julia
Dx = Derivative(Chebyshev()^2,[1,0]) # ∂/∂x
Dy = Derivative(Chebyshev()^2,[0,1]) # ∂/∂y
```

!!! tip
    2番目の引数として静的ベクトルを使用すると、型の安定性が向上します。


# 例

```jldoctest
julia> ∂y = Derivative(Chebyshev()^2, [0,1]);

julia> ∂y * Fun((x,y)->x^2 + y^2) ≈ Fun((x,y)->2y)
true
```
