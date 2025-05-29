```
positive_definite(X::AbstractMatrix{<:Real}, ε = eps(T))
```

厳密に正定値行列であることが制約された`value`を持つパラメータを生成します。引数`X`から`ε`倍の単位行列を引いたものは正定値行列である必要があります（https://en.wikipedia.org/wiki/Definite_matrixを参照）。オプションの第二引数`ε`は正の実数でなければなりません。

制約のないパラメータは、ベクトルとして格納された`LowerTriangular`行列です。
