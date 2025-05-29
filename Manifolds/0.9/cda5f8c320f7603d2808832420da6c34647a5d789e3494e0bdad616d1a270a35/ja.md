```
log(M::CholeskySpace, X, p, q)
```

[`CholeskySpace`](@ref) `M` における対数写像を、正の対角を持つ下三角行列 `p` から `q` への測地線に沿って計算します。式は次のようになります。

$$
\log_p q = ⌊ p ⌋ - ⌊ q ⌋ + \operatorname{diag}(p)\log\bigl(\operatorname{diag}(q)\operatorname{diag}(p)^{-1}\bigr),
$$

ここで $⌊⋅⌋$ は厳密に下三角行列を示し、$\operatorname{diag}$ は対角行列を抽出します。
