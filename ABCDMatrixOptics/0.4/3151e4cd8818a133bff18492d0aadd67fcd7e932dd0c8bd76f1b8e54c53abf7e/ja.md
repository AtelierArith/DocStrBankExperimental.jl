```
propagate(e::Union{Element, Vector{<:Element}}, b)
```

ビーム `b` を単一の要素 `e::Element` または `Vector{<:Element}` によって伝播させます。

戻り値は最終的なビームです。`e * b` としても利用可能です。

## 例

```jldoctest
julia> beam = FreeSpace(10) * GeometricBeam(w=10.0, k=1.0)
GeometricBeam{Float64}(20.0, 1.0, 10.0)

julia> beam = [ThinLens(10), FreeSpace(10)] * GeometricBeam(w=10.0, k=0.0)
GeometricBeam{Float64}(0.0, -1.0, 10.0)

julia> beam.w ≈ 0
true
```
