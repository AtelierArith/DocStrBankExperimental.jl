```
ボクセル空間にグリッドを割り当てます。

# 引数
- `grid::Array{Int, 3}`: 整数グリッド配列。
- `dl::Vector{<:Real}=[1.0, 1.0, 1.0]`: グリッド間隔。
- `start::Vector{<:Real}=[shift[] * 0.5, shift[] * 0.5, shift[] * 0.5]`: 開始点。
```
