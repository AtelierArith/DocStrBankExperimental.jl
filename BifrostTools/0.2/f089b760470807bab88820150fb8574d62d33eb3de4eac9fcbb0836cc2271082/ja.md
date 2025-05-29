```
function xup(
    arr::Array{T,3},
    periodic::Bool=true,
    order::Int=6
) where {T<:AbstractFloat}
```

`arr`に対して5次の多項式補間を用いたスタッガー操作を行い、x方向に変数を半分のグリッドポイント上にシフトします。
