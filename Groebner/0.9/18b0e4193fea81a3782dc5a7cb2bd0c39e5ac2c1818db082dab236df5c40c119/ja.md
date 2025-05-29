```
MatrixOrdering(matrix)
MatrixOrdering(Vector{Vector})
```

行列のモノミアル順序。

## 例

```@example
using Groebner, AbstractAlgebra
R, (x, y, z, w) = QQ["x", "y", "z", "w"];

# 列の数は変数の数と等しい
ord = MatrixOrdering(
    [x,y,z,w],
    [
    1 0  0  2;
    0 0  1  2;
    0 1  1  1;
    ])
groebner([x*y + w, y*z - w], ordering=ord)
```
