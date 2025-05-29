```
eval_length_imaginary_axis(
    β::T,
    Δτ::T
)::Int where {T<:AbstractFloat}
```

逆温度 `β` と虚時間の離散化 `Δτ` が与えられたとき、虚時間軸の長さ `Lτ` を返します。
