```
w, Xi = get_measure(M, t::Int64 = 2*M[:degree]-1 ,lambda = [(-1)^(k-1) for k in 1:M[:nu]])
```

モーメント列の近似を返します $\sum_{i=1}^{\nu} \lambda_i \mu_i$ は、次数 <= t のモーメントに切り捨てられます（デフォルト：緩和の次数の2倍から2を引いたもの）、ディラック測度の重み付き和として：$\sum_{k=1}^{r} \omega_k \delta_{\xi_k}$ ここで

  * `w` はディラック測度の重みのベクトルです。
  * `Xi` は対応するディラック測度のサポート点の $n\times r$ 行列です。列 `Xi[:,i]` は i 番目のディラック測度のサポート点 $\xi_{i}$ であり、その重みは `w[i]` です。

```julia
w, Xi = get_measure(M)

([0.1541368146508854, 0.5889741915171074, 0.256888993597116], [1.4142135624216647 1.414213562080608 1.4142135620270329; -1.732052464639053 1.4141771454788292 1.7319839273833693])
```
