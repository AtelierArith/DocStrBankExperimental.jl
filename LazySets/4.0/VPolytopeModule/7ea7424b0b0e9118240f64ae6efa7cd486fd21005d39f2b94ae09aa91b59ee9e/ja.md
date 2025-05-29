```
VPolytope{N, VN<:AbstractVector{N}, VT<:AbstractVector{VN}} <: AbstractPolytope{N}
```

頂点表現における凸多面体を表す型です。

### フィールド

  * `vertices` – 頂点のリスト

### 例

頂点表現における多面体は、頂点のリストを渡すことで構築できます。例えば、四面体を構築することができます：

```jldoctest
julia> P = VPolytope([[0, 0, 0], [1, 0, 0], [0, 1, 0], [0, 0, 1]]);

julia> P.vertices
4-element Vector{Vector{Int64}}:
 [0, 0, 0]
 [1, 0, 0]
 [0, 1, 0]
 [0, 0, 1]
```

また、`VPolytope`は、各*列*が頂点を表す頂点の行列を渡すことで構築できます：

```jldoctest
julia> M = [0 0 0; 1 0 0; 0 1 0; 0 0 1]'
3×4 adjoint(::Matrix{Int64}) with eltype Int64:
 0  1  0  0
 0  0  1  0
 0  0  0  1

julia> P = VPolytope(M);

julia> P.vertices
4-element Vector{Vector{Int64}}:
 [0, 0, 0]
 [1, 0, 0]
 [0, 1, 0]
 [0, 0, 1]
```
