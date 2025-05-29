```
NFCT{D}
```

NFCT（非等間隔高速コサイン変換）プランで、Dは次元を示します。

NFCTは、離散非等間隔コサイン変換の直接かつ高速な計算を実現します。目的は、与えられた任意のノット $\pmb{x}_j \in [0,0.5]^D, j = 1, \cdots, M$ に対して、

$$
f^c(\pmb{x}_j) = \sum_{\pmb{k} \in I_{\pmb{N},\mathrm{c}}^D} \hat{f}_{\pmb{k}}^c \, \cos(2\pi \, \pmb{k} \odot \pmb{x}_j)
$$

を計算することです。ここで、係数 $\hat{f}^{c}_{\pmb{k}} \in \mathbb{R}$、$\pmb{k} \in I_{\pmb{N},\mathrm{c}}^D \coloneqq \left\{ \pmb{k} \in \mathbb{Z}^D: 1 \leq k_i \leq N_i - 1, \, i = 1,2,\ldots,D \right\}$、およびマルチバンドリミットベクトル $\pmb{N} \in \mathbb{N}^{D}$ を用います。$\cos(\pmb{k} \circ \pmb{x})$ は $\prod_{i=1}^D \cos(k_i \cdot x_i)$ と定義されることに注意してください。転置問題は次のように表されます。

$$
\hat{h}^c_{\pmb{k}} = \sum_{j=1}^M f^c_j \, \cos(2\pi \, \pmb{k} \odot \pmb{x}_j)
$$

ここで、与えられた係数 $f^c_j \in \mathbb{R}, j = 1,2,\ldots,M$ に対して、周波数 $\pmb{k} \in I_{\pmb{N},\mathrm{c}}^D$ を考えます。

# フィールド

  * `N` - 三角多項式 $f^s$ のマルチバンドリミット $(N_1, N_2, \ldots, N_D)$。
  * `M` - ノードの数。
  * `n` - 次元ごとのオーバーサンプリング $(n_1, n_2, \ldots, n_D)$。
  * `m` - ウィンドウサイズ。大きな m はより高い精度をもたらしますが、計算コストも高くなります。
  * `f1` - NFCTフラグ。
  * `f2` - FFTWフラグ。
  * `init_done` - プランが初期化されているかどうかを示します。
  * `finalized` - プランが確定しているかどうかを示します。
  * `x` - ノード $x_j \in [0,0.5]^D, \, j = 1, \ldots, M$。
  * `f` - NFCTのための値 $f^c(\pmb{x}_j)$ または転置NFCTのための係数 $f_j^c \in \mathbb{R}, j = 1, \ldots, M$。
  * `fhat` - NFCTのためのフーリエ係数 $\hat{f}_{\pmb{k}}^c \in \mathbb{R}$ または随伴NFCTのための値 $\hat{h}_{\pmb{k}}^c, \pmb{k} \in I_{\pmb{N},\mathrm{c}}^D$。
  * `plan` - プラン（Cポインタ）。

# コンストラクタ

```
NFCT{D}( N::NTuple{D,Int32}, M::Int32, n::NTuple{D,Int32}, m::Int32, f1::UInt32, f2::UInt32 ) where {D}
```

# 追加コンストラクタ

```
NFCT( N::NTuple{D,Int32}, M::Int32, n::NTuple{D,Int32}, m::Int32, f1::UInt32, f2::UInt32) where {D}
NFCT( N::NTuple{D,Int32}, M::Int32) where {D}
```

# 参照

[`NFCT`](@ref)
