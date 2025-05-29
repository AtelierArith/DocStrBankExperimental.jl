```
LinearMixingModelKernel(k::Kernel, H::AbstractMatrix)
LinearMixingModelKernel(Tk::AbstractVector{<:Kernel},Th::AbstractMatrix)
```

線形混合モデルに関連するカーネルで、`Q` 個のカーネルのベクトルと、`m` 出力を持つ関数のための `Q × m` 混合行列 H を取ります。また、すべての `Q` 基底ベクトルで使用するための単一のカーネル `k` も受け入れます。

# 定義

入力 $x, x'$ および出力次元 $p, p'$ に対して、カーネルは次のように定義されます[^BPTHST]。

$$
k\big((x, p), (x, p')\big) = H_{:,p}K(x, x')H_{:,p'}
$$

ここで、$K(x, x') = Diag(k_1(x, x'), ..., k_Q(x, x'))$ であり、ゼロのオフダイアゴナルエントリを持ちます。$H_{:,p}$ は、$H \in \mathbb{R}^{Q \times m}$ の $p$-列（`p`-出力）であり、$f$ の $m$ 次元出力空間のための $Q$ 基底ベクトルを表します。$k_1, \ldots, k_Q$ は $Q$ 個のカーネルであり、各潜在プロセスに対して1つずつ存在し、$H$ は出力空間をスパンする $Q$ 基底ベクトルの混合行列です。

[^BPTHST]: Wessel P. Bruinsma, Eric Perim, Will Tebbutt, J. Scott Hosking, Arno Solin, Richard E. Turner (2020). [Scalable Exact Inference in Multi-Output Gaussian Processes](https://arxiv.org/pdf/1911.06287.pdf).
