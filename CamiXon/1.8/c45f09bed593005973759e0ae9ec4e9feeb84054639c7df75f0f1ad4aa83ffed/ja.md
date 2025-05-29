```
INSCH!(Z::Vector{Complex{T}}, E::T, grid::CamiDiff.Grid{T}, def::Def{T}) where T<:Real
```

放射波動方程式の最初の $k$ 点に対する *内向き* 積分のための Ansatz 解。ここで $k$ は Adams-Moulton の次数です。この Ansatz は、エネルギー `E` に対する WKB 解に基づいており、上部古典的転回点 - uctp) から *遠く離れた* 距離でのものです。
