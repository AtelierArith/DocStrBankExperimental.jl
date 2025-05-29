```
SteepestDescent(; linsolve = nothing)
```

降下方向を $δu = -Jᵀfu$ として計算します。線形ソルバーと前処理器は、`J` が逆の形で提供されている場合にのみ使用されます。

関連情報としては [`Dogleg`](@ref), [`NewtonDescent`](@ref), [`DampedNewtonDescent`](@ref) があります。
