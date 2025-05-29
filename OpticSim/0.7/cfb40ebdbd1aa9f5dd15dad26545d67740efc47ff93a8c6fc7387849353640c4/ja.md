```
surfaceintersection(bbox::BoundingBox{T}, r::AbstractRay{T,3}) -> Union{EmptyInterval{T},Interval{T}}
```

`r`と軸に整列した[`BoundingBox`](@ref) `bbox`の交差を計算します。

交差がない場合は[`EmptyInterval`](@ref)を返し、交差が1つまたは2つある場合は[`Interval`](@ref)を返します。返される交差のuvは常に**0**であることに注意してください。
