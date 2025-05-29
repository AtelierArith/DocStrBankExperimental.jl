```
dof_satter(lmm::LMM{T}, l::Matrix) where T
```

コントラスト行列 `l` の分母自由度のサッタウェイト近似を返します。

`size(l, 1)` > 1 の場合：

$$
df = \frac{2E}{E - rank(LCL')}
$$

ここで：

  * $$
    LCL' = QΛQ^{-1}
    $$

    とし、$QΛQ^{-1}$ は $LCL'$ のスペクトル分解です。
  * $$
    Lq_i
    $$

    は $Q^{-1}L$ の i 番目の行です。
  * $$
    A = 2H^{-1}
    $$

    、$g = \triangledown_{\theta}(Lq_i C^{-1}_{\theta} Lq_i')$
  * $$
    v_i = \frac{2*Λ_{i,i}^2}{g' * A * g}
    $$
  * $$
    E = \sum_{i=1}^n {\frac{v_i}(v_i - 2)}
    $$

    ただし $v_i > 2$
