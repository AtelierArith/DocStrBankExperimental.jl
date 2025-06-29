```
sc = simplicial_klein_bottle(p::Int)
```

二次元のクライン瓶の三角形分割を作成します。

この関数は、二次元のクライン瓶を表す単体複体を返します。引数 `p` は基礎となる体の特性を指定します。この三角形分割は、Munkresの「代数的トポロジー」における図6.6から取られています。境界の頂点は本に従って文字でラベル付けされており、5つの中心の頂点は `1` から `5` までの数字でラベル付けされています。

# 例

```jldoctest
julia> println(homology(simplicial_klein_bottle(0)))
[1, 1, 0]

julia> println(homology(simplicial_klein_bottle(2)))
[1, 2, 1]

julia> println(homology(simplicial_klein_bottle(3)))
[1, 1, 0]
```
