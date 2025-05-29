```
LatentFactorMOKernel(g::AbstractVector{<:Kernel}, e::MOKernel, A::AbstractMatrix)
```

半パラメトリック潜在因子モデルに関連するカーネル。

# 定義

入力 $x, x'$ および出力次元 $p_x, p_{x'}'$ に対して、カーネルは次のように定義されます[^STJ]

$$
k\big((x, p_x), (x, p_{x'})\big) = \sum^{Q}_{q=1} A_{p_xq}g_q(x, x')A_{p_{x'}q}
                                   + e\big((x, p_x), (x', p_{x'})\big),
$$

ここで、$g_1, \ldots, g_Q$ は $Q$ 個のカーネルであり、各潜在プロセスに対して1つずつ、$e$ は $m$ 出力のためのマルチ出力カーネルであり、$A$ はサイズ $m \times Q$ のカーネルの重みの行列です。

[^STJ]: M. Seeger, Y. Teh, & M. I. Jordan (2005). [Semiparametric Latent Factor Models](https://infoscience.epfl.ch/record/161465/files/slfm-long.pdf).
