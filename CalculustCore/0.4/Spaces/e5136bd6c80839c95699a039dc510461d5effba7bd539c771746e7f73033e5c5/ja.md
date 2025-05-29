```
massOp(V::AbstractSpace, discr::AbstractDiscretization)
```

質量演算子: ∫⋅dx

離散化スキーム `discr` の質量行列を表します。

`Galerkin` 離散化の場合、`[ij]` 番目のエントリは `i` 番目と `j` 番目の基底関数の内積に対応します。

$$
[M]_{ij} = \int_\Omega \phi_i(x)\phi_j(x) dx = \langle \phi_i, \phi_j \rangle
$$
