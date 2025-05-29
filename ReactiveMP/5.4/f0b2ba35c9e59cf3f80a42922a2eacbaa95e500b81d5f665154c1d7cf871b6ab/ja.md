```
StandardBasisVector{T, len, ind}(scale::T)
```

`StandardBasisVector`は、長さ`len`のゼロの標準直交基底ベクトルを作成し、インデックス`ind`に単一の要素`scale`を持ちます。

例として、第一次元の3次元標準基底ベクトルは次のようになります。

$$
e = \begin{bmatrix} 1 \\ 0 \\ 0 \end{bmatrix}
$$

これは、`e = StandardBasisVector(3, 1, 1)`と呼び出すことで構築できます。
