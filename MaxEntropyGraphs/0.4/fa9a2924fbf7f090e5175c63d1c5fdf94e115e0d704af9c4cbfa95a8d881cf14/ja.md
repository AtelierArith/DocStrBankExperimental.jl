```
project(B::T; layer::Symbol=:bottom, method::Symbol=:simple) where {T<:AbstractMatrix}
```

二部隣接行列 `B` をその層の一つに射影します。

# 引数

  * `layer`: 層は `layer=:bottom` または `layer=:top` を渡すことで指定できます。層のメンバーシップはグラフの二部マップによって決定されます。
  * `method`: 射影されたグラフの隣接行列を計算するために使用される方法です。これは `:simple` または `:weighted` である可能性があります。両方の方法は、二部隣接行列とその転置の積を計算しますが、`:weighted` 方法は射影されたグラフの辺の重みを使用します。

# 例

```jldoctest project_bipartite_matrix
julia> B = [0 0 0 1 1; 0 0 0 1 1; 0 0 0 1 0];

julia> project(B, layer=:bottom)
3×3 Matrix{Bool}:
 0  1  1
 1  0  1
 1  1  0

```

```jldoctest project_bipartite_matrix
julia> project(B, layer=:top)
5×5 Matrix{Bool}:
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  1
 0  0  0  1  0

```

```jldoctest project_bipartite_matrix
julia> B = [0 0 0 1 1; 0 0 0 1 1; 0 0 0 1 0];

julia> project(B, layer=:bottom, method=:weighted)
3×3 Matrix{Int64}:
 0  2  1
 2  0  1
 1  1  0

```

```jldoctest project_bipartite_matrix
julia> project(B, layer=:top, method=:weighted)
5×5 Matrix{Int64}:
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  0
 0  0  0  0  2
 0  0  0  2  0

```
