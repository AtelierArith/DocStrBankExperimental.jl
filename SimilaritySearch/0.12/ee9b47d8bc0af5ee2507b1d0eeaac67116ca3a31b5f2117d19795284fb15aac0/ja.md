```
LpDistance(p)
LpDistance(p, pinv)
```

一般的なミンコフスキー距離 $L_p$ 距離は次のように定義されます。

$$
L_p(u, v) = \left|\sum_i{(u_i - v_i)^p}\right|^{1/p}
$$

ここで、$p_{inv} = 1/p$ です。特定の動作が必要な場合は、無関係な `p` と `pinv` を指定できることに注意してください。
