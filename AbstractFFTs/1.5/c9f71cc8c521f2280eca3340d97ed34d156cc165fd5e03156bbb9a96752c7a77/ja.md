```
ifft(A [, dims])
```

多次元逆FFT。

一次元逆FFTは次のように計算します。

$$
\operatorname{IDFT}(A)[k] = \frac{1}{\operatorname{length}(A)}
\sum_{n=1}^{\operatorname{length}(A)} \exp\left(+i\frac{2\pi (n-1)(k-1)}
{\operatorname{length}(A)} \right) A[n].
$$

多次元逆FFTは、単に`A`の各変換次元に沿ってこの操作を実行します。
