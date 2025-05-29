```
QZZB(x::AbstractVector, p::AbstractVector, rho::AbstractVecOrMat; eps=GLOBAL_EPS)
```

量子Ziv-Zakai境界（QZZB）の計算。

  * `x`: 積分のためのパラメータの範囲。
  * `p`: 事前分布。
  * `rho`: パラメータ化された密度行列。
  * `eps`: マシンイプシロン。

```
