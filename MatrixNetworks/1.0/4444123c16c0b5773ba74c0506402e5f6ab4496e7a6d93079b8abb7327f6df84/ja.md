  * triangles(A) はグラフ A のすべての三角形のイテレータを返します
  * triangles(A,i) はノード i を含むグラフ A のすべての三角形のイテレータを返します
  * triangles(A,S) は集合 S のノードを含むグラフ A のすべての三角形のイテレータを返します
  * triangles(A,S;symmetries=true) は対称性を持つ集合 S のノードを含むグラフ A のすべての三角形のイテレータを返します（すなわち、三角形 (i,j,k) は 6 回カウントされます）

## サンプル実行:

```
A = load_matrix_network("clique-10");
mytriangles = triangles(A)
for tri in mytriangles
    MatrixNetworks.triprint(tri)
end
z = collect(mytriangles)
ei,ej,ek = unzip_triangles(z)
```

## 最初の三角形にアクセスするための簡単な例:

```
julia> tri = first(mytriangles)
MatrixNetworks.tri_struct(1, 2, 3)

julia> tri.v1,tri.v2,tri.v3
(1, 2, 3)
```
