```
treated_ids(x <: BalancedPanel)

パネル内の処理単位のインデックスを返します。これにより、Y[treated_ids(x), :] は、すべての期間における処理単位の結果の (Nₜᵣ×T) 行列を返します。
```
