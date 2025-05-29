```
VPolygon{N, VN<:AbstractVector{N}} <: AbstractPolygon{N}
```

頂点によって多角形を表す型です。

### フィールド

  * `vertices` – 頂点のリスト

### 注意事項

この型は、すべての頂点が反時計回りにソートされていると仮定します。

この特性を保証するために、`VPolygon`のコンストラクタはデフォルトで頂点に対して凸包アルゴリズムを実行します。これにより冗長な頂点も削除されます。頂点がソートされていることがわかっている場合は、フラグ`apply_convex_hull=false`を使用してこの前処理をスキップできます。

### 例

頂点表現の多角形は、頂点のリストを渡すことで構築できます。たとえば、次のように直角三角形を構築できます。

```jldoctest polygon_vrep
julia> P = VPolygon([[0, 0], [1, 0], [0, 1]]);

julia> P.vertices
3-element Vector{Vector{Int64}}:
 [0, 0]
 [1, 0]
 [0, 1]
```

また、各*列*が頂点を表す頂点の行列を渡すことで`VPolygon`を構築することもできます。

```jldoctest polygon_vrep
julia> M = [0 1 0; 0 0 1.]
2×3 Matrix{Float64}:
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> P = VPolygon(M);

julia> P.vertices
3-element Vector{Vector{Float64}}:
 [0.0, 0.0]
 [1.0, 0.0]
 [0.0, 1.0]
```
