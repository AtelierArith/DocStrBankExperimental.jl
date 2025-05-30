```
matrix(a::ExprOp, site::AbstractSite...)
```

与えられたサイトのための一般的な演算子の行列を返します。サイトがすべて同一である場合は、1つだけ指定することができます。

# 例

```
matrix(X, Qubit())
matrix(Swap, Qubit())
matrix(X⊗A, Qubit(), Boson(2))
```
