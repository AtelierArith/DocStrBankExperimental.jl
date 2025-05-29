```
NFST{D}
```

NFST（非等間隔高速サイン変換）プランで、Dは次元を表します。

NFSTは、離散非等間隔サイン変換の直接的かつ高速な計算を実現します。目的は、与えられた任意のノット $\pmb{x}_j \in [0,0.5]^D, j = 1, \cdots, M$ に対して、係数 $\hat{f}^{s}_{\pmb{k}} \in \mathbb{R}$、$\pmb{k} \in I_{\pmb{N},\mathrm{s}}^D \coloneqq \left\{ \pmb{k} \in \mathbb{Z}^D: 1 \leq k_i \leq N_i - 1, \, i = 1,2,\ldots,D \right\}$ を用いて

$$
f^s(\pmb{x}_j) = \sum_{\pmb{k} \in I_{\pmb{N},\mathrm{s}}^D} \hat{f}_{\pmb{k}}^s \, \sin(2\pi \, \pmb{k} \odot \pmb{x}_j)
$$

を計算することです。なお、$\sin(\pmb{k} \circ \pmb{x}) \coloneqq \prod_{i=1}^D \sin(k_i \cdot x_i)$ と定義します。転置問題は次のように表されます。

$$
\hat{h}^s_{\pmb{k}} = \sum_{j=1}^M f^s_j \, \sin(2\pi \, \pmb{k} \odot \pmb{x}_j)
$$

与えられた係数 $f^s_j \in \mathbb{R}, j = 1,2,\ldots,M$ に対して、周波数 $\pmb{k} \in I_{\pmb{N},\mathrm{s}}^D$ で表されます。

# フィールド

  * `N` - 三角多項式 $f^s$ のマルチバンドリミット $(N_1, N_2, \ldots, N_D)$。
  * `M` - ノードの数。
  * `n` - 次元ごとのオーバーサンプリング $(n_1, n_2, \ldots, n_D)$。
  * `m` - ウィンドウサイズ。大きな m はより高い精度をもたらしますが、計算コストも高くなります。
  * `f1` - NFSTフラグ。
  * `f2` - FFTWフラグ。
  * `init_done` - プランが初期化されているかどうかを示します。
  * `finalized` - プランが確定しているかどうかを示します。
  * `x` - ノード $x_j \in [0,0.5]^D, \, j = 1, \ldots, M$。
  * `f` - NFSTのための値 $f^s(\pmb{x}_j)$ または転置NFSTのための係数 $f_j^s \in \mathbb{R}, j = 1, \ldots, M$。
  * `fhat` - NFSTのためのフーリエ係数 $\hat{f}_{\pmb{k}}^s \in \mathbb{R}$ または随伴NFSTのための値 $\hat{h}_{\pmb{k}}^s, \pmb{k} \in I_{\pmb{N},\mathrm{s}}^D$。
  * `plan` - プラン（Cポインタ）。

# コンストラクタ

```
NFST{D}( N::NTuple{D,Int32}, M::Int32, n::NTuple{D,Int32}, m::Int32, f1::UInt32, f2::UInt32 ) where {D}
```

# 追加コンストラクタ

```
NFST( N::NTuple{D,Int32}, M::Int32, n::NTuple{D,Int32}, m::Int32, f1::UInt32, f2::UInt32) where {D}
NFST( N::NTuple{D,Int32}, M::Int32) where {D}
```

# 参照

[`NFST`](@ref)
