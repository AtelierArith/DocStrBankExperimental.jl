```
constrain_KVL(m, net::Network{MultiPhase})
```

バス間の電圧降下定義を追加します。

$$
w_j = w_i - S_{ij} Z^{\star} - Z S_{ij}^{\star} + Z L_{ij} Z^{\star}
$$
