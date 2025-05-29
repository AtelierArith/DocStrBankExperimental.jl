```
LpDistance(p)
LpDistance(p, pinv)
```

The general Minkowski distance $L_p$ distance is defined as

$$
L_p(u, v) = \left|\sum_i{(u_i - v_i)^p}\right|^{1/p}
$$

Where $p_{inv} = 1/p$. Note that you can specify unrelated `p` and `pinv` if you need an specific behaviour.
