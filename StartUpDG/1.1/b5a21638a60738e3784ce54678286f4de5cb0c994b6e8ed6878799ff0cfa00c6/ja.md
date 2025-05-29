```
struct MeshData{Dim, Tv, Ti}
```

MeshData: 非構造メッシュ上の高次分割多項式離散化に関する情報を含みます。

例:

```julia
N, K1D = 3, 2
rd = RefElemData(Tri(), N)
VXY, EToV = uniform_mesh(Tri(), K1D)
md = MeshData(VXY, EToV, rd)
(; x, y ) = md
```
