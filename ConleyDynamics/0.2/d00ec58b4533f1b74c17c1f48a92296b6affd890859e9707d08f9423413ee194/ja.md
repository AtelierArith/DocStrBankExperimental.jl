```
sc = simplicial_torus(p::Int)
```

二次元トーラスの三角形分割を作成します。

この関数は、二次元トーラスを表す単体複体を返します。引数 `p` は基礎となる体の特性を指定します。この三角形分割は、Munkresの「代数的トポロジー」における図6.4から取られています。境界の頂点は書籍と同様に文字でラベル付けされており、中央の5つの頂点は `1` から `5` でラベル付けされています。

# 例

```jldoctest
julia> println(homology(simplicial_torus(0)))
[1, 2, 1]

julia> println(homology(simplicial_torus(2)))
[1, 2, 1]

julia> println(homology(simplicial_torus(3)))
[1, 2, 1]
```
