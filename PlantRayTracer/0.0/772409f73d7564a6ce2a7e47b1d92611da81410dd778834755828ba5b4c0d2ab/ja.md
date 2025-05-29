```
Naive(tris::Vector{Triangle{FT}}, ids::Vector{Int}, rule) where {FT}
```

シーンをグローバルバウンディングボックスにラップします（加速なし）。シーン内の三角形と、各三角形を対応するマテリアルオブジェクトにリンクするIDが与えられます。引数 `rule` は `BVH` との互換性のために残されており、何も行いません。

## 例

```jldoctest
julia> using PlantGeomPrimitives

julia> tris = PlantRayTracer.Triangle(Ellipse());

julia> ids  = repeat([1], length(tris));

julia> Naive(tris, ids);
```
