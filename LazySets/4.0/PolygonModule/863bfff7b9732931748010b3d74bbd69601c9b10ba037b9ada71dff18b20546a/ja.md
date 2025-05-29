```
Polygon{N, VN<:AbstractVector{N}} <: LazySet{N}
```

頂点によって非凸多角形を表す型です。

### フィールド

  * `vertices` – 頂点のリスト（時計回りまたは反時計回りの順序）

### 例

頂点表現の非凸多角形は、頂点のリストを渡すことで構築できます。例えば、歯を作ることができます：

```jldoctest polygon_v_ncrep
julia> P = Polygon([[0.0, 0], [0, 2], [2, 2], [2, 0], [1, 1]]);

julia> P.vertices
5-element Vector{Vector{Float64}}:
 [0.0, 0.0]
 [0.0, 2.0]
 [2.0, 2.0]
 [2.0, 0.0]
 [1.0, 1.0]
```
