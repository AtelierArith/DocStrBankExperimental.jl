```
check_rank_one(m::JuMP.AbstractModel, net::Network, tol=1e-3)
```

`m[:H]` 行列のランクをPSDコーン制約からチェックします。警告はランクが1より大きい値を示します。
