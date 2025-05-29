```
tensor(a::ExprOp, site::AbstractSite...)
```

与えられたサイトのための一般的な演算子のITensorを返します。サイトがすべて同一である場合は、1つだけを指定することができます。

# 例

```
tensor(X, Qubit())
tensor(Swap, Qubit())
tensor(X⊗A, Qubit(), Boson(2))
```
