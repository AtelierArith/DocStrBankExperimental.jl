```
PointsFromMatrix(A [,i1=1,i2=2])
```

これは、行インデックスi1とi2を使用して、行列から2次元の点のタプルを暗黙的に抽出します。行列の列は個々の点になります。

```
PointsFromMatrix(A) == vec(reinterpret(Tuple{Int,Int},A[1:2,:]))
```

この関数は、行列をDelaunatorの点のセットに透過的にマッピングするために使用できます。（コピーは行われません）。

## 例

```
A = reshape(1:20, 4, 5)
rval = triangulate(PointsFromMatrix(A))) # uses A[1:2,:]
```
