```
exp(M::CholeskySpace, p, X)
```

[`CholeskySpace`](@ref) `M`から、正の対角を持つ下三角行列 `p` から下三角行列 `X` への指数写像を計算します。式は次のようになります。

$$
\exp_p X = ⌊ p ⌋ + ⌊ X ⌋ + \operatorname{diag}(p)
\operatorname{diag}(p)\exp\bigl( \operatorname{diag}(X)\operatorname{diag}(p)^{-1}\bigr),
$$

ここで、$⌊⋅⌋$ は厳密に下三角行列を示し、$\operatorname{diag}$ は対角行列を抽出します。
