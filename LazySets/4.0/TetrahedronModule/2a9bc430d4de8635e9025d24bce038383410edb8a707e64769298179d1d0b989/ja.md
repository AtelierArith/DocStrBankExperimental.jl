```
Tetrahedron{N, VN<:AbstractVector{N}, VT<:AbstractVector{VN}} <: AbstractPolytope{N}
```

頂点表現における（3次元の）テトラヘドロンを表す型です。

### フィールド

  * `vertices` – 頂点のリスト

### 例

テトラヘドロンは、頂点のリストを渡すことで構築できます。以下は、[ウィキペディアのテトラヘドロンのページ](https://en.wikipedia.org/wiki/Tetrahedron)からエッジの長さが2のテトラヘドロンを構築します。

```jldoctest
julia> vertices = [[1, 0, -1/sqrt(2)], [-1, 0, -1/sqrt(2)], [0, 1, 1/sqrt(2)], [0, -1, 1/sqrt(2)]];

julia> T = Tetrahedron(vertices);

julia> dim(T)
3

julia> zeros(3) ∈ T
true

julia> σ(ones(3), T)
3-element Vector{Float64}:
 0.0
 1.0
 0.7071067811865475
```
