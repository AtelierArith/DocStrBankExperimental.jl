```
Geomin(epsilon = 0.01)
```

*Geomin*回転法。

## 詳細

*Geomin*は、二乗負荷の列ごとの幾何平均の合計を最小化する傾斜回転法です：

$$
Q_{\mathrm{Geomin}}(Λ, ε) =
    ∑_{i = 1}^p \left(\prod_{j = 1}^k λ²_{i, j} + ε \right)^{\frac{1}{k}}.
$$

## キーワード引数

  * `epsilon`: ゼロ負荷に対処するための小さな非負定数。
