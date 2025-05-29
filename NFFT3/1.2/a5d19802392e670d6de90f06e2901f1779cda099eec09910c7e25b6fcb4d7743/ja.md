```
NFFT{D}
```

NFFT（非等間隔高速フーリエ変換）プランで、Dは次元を表します。

D次元の三角多項式を考えます。

$$
f \colon \mathbb{T}^D \to \mathbb{C}, \; f(\pmb{x}) \colon = \sum_{\pmb{k} \in I_{\pmb{N}}^D} \hat{f}_{\pmb{k}} \, \mathrm{e}^{-2 \pi \mathrm{i} \, \pmb{k} \cdot \pmb{x}}
$$

インデックス集合 $I_{\pmb{N}}^D \coloneqq \left\{ \pmb{k} \in \mathbb{Z}^D: - \frac{N_i}{2} \leq k_i \leq \frac{N_i}{2} - 1, \, i = 1,2,\ldots,D \right\}$ で、$\pmb{N} \in (2\mathbb{N})^{D}$ はマルチバンドリミットです。NDFT（非等間隔離散フーリエ変換）は、$M \in \mathbb{N}$ の任意の点 $\pmb{x}_j \in [-0.5,0.5)^D$ における評価です（$j = 1, \ldots, M$）。

$$
f(\pmb{x}_j) \colon = \sum_{\pmb{k} \in I^D_{\pmb{N}}} \hat{f}_{\pmb{k}} \, \mathrm{e}^{-2 \pi \mathrm{i} \, \pmb{k} \cdot \pmb{x}_j}
$$

与えられた係数 $\hat{f}_{\pmb{k}} \in \mathbb{C}$ に対して。NFFTはNDFTの高速評価と、随伴問題である随伴NDFTの高速評価のためのアルゴリズムです。

$$
\hat{h}_{\pmb{k}} \coloneqq \sum^{M}_{j = 1} f_j \, \mathrm{e}^{-2 \pi \mathrm{i} \, \pmb{k} \cdot \pmb{x}_j}, \, \pmb{k} \in I_{\pmb{N}}^D,
$$

与えられた係数 $f_j \in \mathbb{C}, j =1,2,\ldots,M$ に対して。一般に、随伴NDFTはNDFTの逆変換ではないことに注意してください。

# フィールド

  * `N` - 三角多項式 $f$ のマルチバンドリミット $(N_1, N_2, \ldots, N_D)$。
  * `M` - ノードの数。
  * `n` - 次元ごとのオーバーサンプリング $(n_1, n_2, \ldots, n_D)$。
  * `m` - ウィンドウサイズ。mが大きいほど精度が向上しますが、計算コストも高くなります。
  * `f1` - NFFTフラグ。
  * `f2` - FFTWフラグ。
  * `init_done` - プランが初期化されているかどうかを示します。
  * `finalized` - プランが確定しているかどうかを示します。
  * `x` - ノード $\pmb{x}_j \in [-0.5,0.5)^D, j = 1, \ldots, M$。
  * `f` - NFFTのための値 $f(\pmb{x}_j)$ または随伴NFFTのための係数 $f_j \in \mathbb{C}, j = 1, \ldots, M$。
  * `fhat` - NFFTのためのフーリエ係数 $\hat{f}_{\pmb{k}} \in \mathbb{C}$ または随伴NFFTのための値 $\hat{h}_{\pmb{k}}, \pmb{k} \in I_{\pmb{N}}^D$。
  * `plan` - プラン（Cポインタ）。

# コンストラクタ

```
NFFT{D}( N::NTuple{D,Int32}, M::Int32, n::NTuple{D,Int32}, m::Int32, f1::UInt32, f2::UInt32 ) where D
```

# 追加コンストラクタ

```
NFFT( N::NTuple{D,Int32}, M::Int32, n::NTuple{D,Int32}, m::Int32, f1::UInt32, f2::UInt32 ) where {D}
NFFT( N::NTuple{D,Int32}, M::Int32 ) where {D}
```
