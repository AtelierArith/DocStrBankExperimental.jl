```
gram_schmidt_orthogonalisation(x::QQMatrix)
```

$$
x
$$

の列を$\mathbb{Q}^m$の部分集合の生成子として取り、同じ部分空間の直交生成集合を持つ行列を返します。

# 例

```jldctest
julia> S = matrix_space(QQ, 3, 3);

julia> A = S([4 7 3; 2 9 1; 0 5 3])
[4   7   3]
[2   9   1]
[0   5   3]

julia> B = gram_schmidt_orthogonalisation(A)
[4   -11//5     95//123]
[2    22//5   -190//123]
[0        5    209//123]
```
