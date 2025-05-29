```
NFMT{D}
```

Dが次元であるNFMT（非等間隔ファースト混合変換）プラン。

NFCTは、離散非等間隔混合変換の直接かつ高速な計算を実現します。目的は次の計算を行うことです。

$$
f^{\pmb{d}}(\pmb{x}_j) \coloneqq \sum_{\pmb{k} \in I_{\pmb{N},\pmb{d}}^d} \hat{f}_{\pmb{k}}^{\pmb{d}} \, \phi_{\pmb{k}}^{\pmb{d}}(\pmb{x}_j)
$$

次のように定義されます。

$$
\phi_{\pmb{k}}^{\pmb{d}}(\pmb{x})=\prod_{j=1}^d\begin{cases}1,&k_j=0\\\exp(2\pi\mathrm{i}k_jx_j),&d_j=\exp,\;k_j\neq0\\
\sqrt{2}\cos(\pi k_jx_j),&d_j=\cos,\;k_j\neq0\\
\sqrt{2}\cos(k_j\arccos(2x_j-1)),&d_j=\mathrm{alg},\;k_j\neq0\end{cases}
$$

ここで、$\pmb{d}\in\{\exp,\cos,\mathrm{alg}\}^d$は与えられた任意のノット$\pmb{x}_j \in [0,1]^D, j = 1, \cdots, M$に対して、係数$\hat{f}^{c}_{\pmb{k}} \in \mathbb{R}$を持ちます。

$$
\pmb{k}\inI_{\pmb{N},\pmb{d}}^d \coloneqq \overset{d}{\underset{j=1}{\vphantom{\mathop{\raisebox{-.5ex}{\hbox{\huge{$\times$}}}}}⨉}}\begin{cases}\Big\{-\frac{N_j}{2},-\frac{N_j}{2}+1,\ldots,\frac{N_j}{2}\Big\},&d_j=\exp\\\Big\{0,1,\ldots,\frac{N_j}{2}\Big\},&d_j\neq\exp\end{cases},
$$

およびマルチバンドリミットベクトル$\pmb{N} \in (2\mathbb{N})^{D}$。転置問題は次のように表されます。

$$
\hat{h}^{\pmb{d}}_{\pmb{k}} = \sum_{j=1}^M f^{\pmb{d}}_j \, \phi_{\pmb{k}}^{\pmb{d}}(\pmb{x}_j)
$$

周波数$\pmb{k} \in I_{\pmb{N},\pmb{d}}^D$に対して、与えられた係数$f^{\pmb{d}}_j \in \mathbb{R}, j = 1,2,\ldots,M$を持ちます。

# フィールド

  * `basis_vect` - 各次元の基底（`exp`, `cos`, `alg`）を持つタプル
  * `NFFT_struct` - 基盤となる[NFFTプラン](@ref NFFT_site# Plan structure)。

# コンストラクタ

```
NFMT{D}( basis_vect::NTuple{D,String}, P::NFFT{D}N::NTuple{D,Int32}) where {D}
```

> **警告**: 直接使用するためのものではありません！


# 追加コンストラクタ

```
NFMT( N::NTuple{D,Int32}, M::Int32, n::NTuple{D,Int32}, m::Int32, f1::UInt32, f2::UInt32) where {D}
NFMT( N::NTuple{D,Int32}, M::Int32) where {D}
```

次のように定義されます。

  * `N` - 三角多項式$f^s$のマルチバンドリミット$(N_1, N_2, \ldots, N_D)$。
  * `M` - ノードの数。
  * `n` - 各次元のオーバーサンプリング$(n_1, n_2, \ldots, n_D)$。
  * `m` - ウィンドウサイズ。大きなmはより高い精度をもたらしますが、計算コストも高くなります。
  * `f1` - NFSTフラグ。
  * `f2` - FFTWフラグ。

# 参照

[NFMT`](@ref) ```
