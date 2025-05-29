```
r_scale(c::Real,β::AbstractVector{<:Real},α::AbstractVector{<:Real})
```

正の重み $m(t)$ に関して直交する直交多項式の系の再帰係数 `(α,β)` が与えられたとき、この関数は正の $c$ に対するスケールされた測度 $c m(t)$ のための再帰係数 `(α_,β_)` を返します。
