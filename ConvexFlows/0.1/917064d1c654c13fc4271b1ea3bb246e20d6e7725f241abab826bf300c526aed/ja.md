```
Ubar(obj::Objective, ν)
```

目的関数 `objective` のネットフロー効用関数の「共役」を `ν` で評価します。具体的には、

$$
    \bar U(\nu) = \sup_y \left(U(y) - \nu^T y \right).
$$
