```
struct Boundary{S<:Symbol, UR<:UnitRange{<:Integer}}
    name::S         # 境界パッチ名
    IDs_range::UR   # 境界情報（面とboundary_cellsID）にアクセスするための範囲
end
```
