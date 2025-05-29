```
dof_satter(lmm::LMM{T}, l) where T
```

サタースウェイト近似を返します。分母の自由度は、`l` がコントラストベクトル（固定効果係数ベクトル（`β`）の推定可能な線形結合）である場合です。

$$
df = \frac{2(LCL')^{2}}{g'Ag}
$$

ここで: $A = 2H^{-1}$, $g = \triangledown_{\theta}(LC^{-1}_{\theta}L')$
