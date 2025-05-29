```
function chand_recursion(y::Matrix{S}, T::Matrix{S}, R::Matrix{S}, C::Vector{S},
                         Q::Matrix{S}, Z::Matrix{S}, D::Vector{S}, H::Matrix{S},
                         s_pred::Vector{S} = Vector{S}(0),
                         P_pred::Matrix{S} = Matrix{S}(0,0);
                         allout::Bool = false, Nt0::Int = 0,
                         tol::Float64 = 0.0) where {S<:AbstractFloat}
```

チャンドラセカール再帰の実装、線形ガウス状態空間システムにおける尤度評価のための高速アルゴリズム。エド・ハーバストによるコードに基づいています。

状態遷移方程式：

```
s_t = TT * s_{t-1} + RR * ε_t, ε_t ~ iid N(0, QQ)
```

測定方程式：

```
y_t = DD + ZZ * s_t + η_t, η_t ~ iid N(0, HH)
```

対数尤度評価を返します。
