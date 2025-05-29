```
DiscreteFourierFeature(in_dims::Int, out_dims::Int, N::Int, period::Real)
```

[lindell2021bacon](@cite)で提案された離散フーリエフィルタ。周期$P$の周期関数に対して、振幅-位相形式のフーリエ級数は次のようになります。

$$
s_N(x)=\frac{a_0}{2}+\sum_{n=1}^N{a_n}\cdot \sin \left( \frac{2\pi}{P}nx+\varphi _n \right)
$$

出力は周期的であることが保証されています。

## 引数

  * `in_dims`: 入力次元の数。
  * `out_dims`: 出力次元の数。
  * `N`: 式中の$N$。
  * `period`: 式中の$P$。

```
