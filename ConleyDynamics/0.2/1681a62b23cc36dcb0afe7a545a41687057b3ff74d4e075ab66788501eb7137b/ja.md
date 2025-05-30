```
sc = simplicial_projective_plane(p::Int)
```

射影平面の三角形分割を作成します。

この関数は射影平面を表す単体複体を返します。引数 `p` は基礎となる体の特性を指定します。この三角形分割は、Munkresの代数的トポロジーに関する本の図6.6から取られています。境界の頂点は本と同様に文字でラベル付けされており、5つの中心の頂点は `1` から `5` までの数字でラベル付けされています。

# 例

```jldoctest
julia> println(homology(simplicial_projective_plane(0)))
[1, 0, 0]

julia> println(homology(simplicial_projective_plane(2)))
[1, 1, 1]

julia> println(homology(simplicial_projective_plane(3)))
[1, 0, 0]
```
