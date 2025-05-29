```
svd(A; full::Bool = false, alg::Algorithm = default_svd_alg(A)) -> SVD

特異値分解 (SVD) `AbstractMultipliableMatrix` の。
均一行列にのみ存在します (pp. 124, Hart, 1995)。
`SVD{AbstractMultipliableMatrix}` オブジェクトの関数: `inv`, `size`, `adjoint`, `svdvals`。
未実装: `ldiv!`。
```
