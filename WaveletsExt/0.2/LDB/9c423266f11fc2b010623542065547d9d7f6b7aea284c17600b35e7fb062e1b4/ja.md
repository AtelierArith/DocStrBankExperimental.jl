```
EarthMoverDistance <: SignaturesDM
```

Earth Mover Distance は Signatures エネルギーマップの識別測度です。

方程式:

$$
E(P,Q) = \frac{\sum_{k=1}^{m+n+1} |\hat p_k - \hat q_k| (r_{k+1} - r_k)}{w_\Sigma}
$$

ここで

  * $$
    r_1, r_2, \ldots, r_{m+n}
    $$

    は $p_1, \ldots, p_m, q_1, \ldots, q_n$ のソートされたリストです
  * $$
    \hat p_k = \sum_{p_i \leq r_k} w_{p_i}
    $$
  * $$
    \hat q_k = \sum_{q_i \leq r_k} w_{q_i}
    $$
