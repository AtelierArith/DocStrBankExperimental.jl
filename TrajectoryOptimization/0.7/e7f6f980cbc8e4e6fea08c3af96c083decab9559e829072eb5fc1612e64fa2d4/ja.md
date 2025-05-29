```
LQRCost(Q, R, xf, [uf; kwargs...])
```

`QuadraticCostFunction`の便利なコンストラクタで、次の形式を持ちます：

$$
\frac{1}{2} (x-x_f)^T Q (x-xf) + \frac{1}{2} (u-u_f)^T R (u-u_f)
$$

$$
Q
$$

と$R$が対角行列である場合、出力は`DiagonalCost`になります。それ以外の場合は`QuadraticCost`になります。
