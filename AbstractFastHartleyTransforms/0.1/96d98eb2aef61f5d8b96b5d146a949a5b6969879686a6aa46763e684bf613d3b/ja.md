```
ifft(A [, dims])
```

多次元逆FHT。

1次元逆FHTは、次のように定義される1次元逆DHT（IDHT）を計算します。

$$
\operatorname{IDHT}(A)[k] = \frac{1}{\operatorname{length}(A)} \operatorname{DHT}(A)[k]
$$

多次元逆FHTは、単に`A`の各変換次元に沿ってこの操作を実行します。
