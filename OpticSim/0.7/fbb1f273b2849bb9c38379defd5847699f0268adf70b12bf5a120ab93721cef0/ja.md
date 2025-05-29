```
surfaceintersection(surf::Surface{T}, r::AbstractRay{T}) where {T}
```

`r`と任意のタイプの表面`suf`との交差を計算します。いくつかの表面は解析的に交差できないため、交差させるためには[`AcceleratedParametricSurface`](@ref)でラップする必要があります。

交差がない場合は[`EmptyInterval`](@ref)を返し、1つまたは2つの交差がある場合は[`Interval`](@ref)を返し、2つ以上の交差がある場合は[`DisjointUnion`](@ref)を返します。
