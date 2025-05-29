```
IntrinsicCoregionMOKernel(; kernel::Kernel, B::AbstractMatrix)
```

内因的コレギオナリゼーションモデルに関連するカーネル。

# 定義

入力 $x, x'$ および出力次元 $p, p'$ に対して、カーネルは次のように定義されます[^ARL]

$$
k\big((x, p), (x', p'); B, \tilde{k}\big) = B_{p, p'} \tilde{k}\big(x, x'\big),
$$

ここで $B$ はサイズ $m \times m$ の正定値半定行列であり、$m$ は出力の数、$\tilde{k}$ は潜在プロセスによって共有されるスカラー値カーネルです。

[^ARL]: M. Álvarez, L. Rosasco, & N. Lawrence (2012). [Kernels for Vector-Valued Functions: a Review](https://arxiv.org/pdf/1106.6251.pdf).
