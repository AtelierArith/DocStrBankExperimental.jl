```
ssb_posvel_pN(μ, q)
```

太陽系重心（SSB）を決定するために必要な2つの和を返します。

$$
\left\lbrace
\begin{array}{l}
    \sum_i \mu_i^*\mathbf{r}_i = \mathbf{0} \\
    \sum_i \mu_i^*\dot{\mathbf{r}}_i + \dot{\mu}_i^*\mathbf{r}_i = \mathbf{0},
\end{array}
\right.
$$

および `q` に含まれるすべての天体の質量パラメータの和

$$
\sum_i\mu_i^*, 
$$

ここで、$\mathbf{r}_i$, $\mathbf{v}_i = \dot{\mathbf{r}}_i$ および $\mu_i^*$ は `i` 番目の天体の重心位置、重心速度および質量パラメータ（相対論的補正を $1/c^2$ のオーダーまで含む）です。

https://doi.org/10.1051/0004-6361:20066607 の式 (5) を参照してください。

また、[`μ_star_fun`](@ref) も参照してください。

# 引数

  * `μ`: 質量パラメータのベクトル。
  * `q`: 位置 + 速度 + 月の物理的リブラション + TT-TDB のベクトル。
