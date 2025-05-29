```
doesintersect(bbox::BoundingBox{T}, r::AbstractRay{T,3}) -> Bool
```

`r`が軸に整列した[`BoundingBox`](@ref)である`bbox`と交差するかどうかをテストします。
