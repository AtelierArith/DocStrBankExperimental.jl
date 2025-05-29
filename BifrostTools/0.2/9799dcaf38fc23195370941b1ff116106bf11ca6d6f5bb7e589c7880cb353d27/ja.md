```
function yup(
    arr::Array{T,3},
    periodic::Bool=true,
    order::Int=6
) where {T<:AbstractFloat}
```

`arr`に対して5次の多項式補間によるスタッガー操作を行い、変数をy方向に半分のグリッドポイント上にシフトします。
