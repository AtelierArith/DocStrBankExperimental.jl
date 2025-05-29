```
FASTSUM
```

高速総和アルゴリズムは、次の関数を評価します。

$$
f(\pmb{y}) \coloneqq \sum^{N}_{k = 1} \alpha_k \, \mathscr{K}(\pmb{y} - \pmb{x}_k) = \sum^{N}_{k = 1} \alpha_k \, K(\lVert \pmb{y} - \pmb{x}_k \rVert_2)
$$

与えられた任意のソースノット $\pmb{x}_k \in \mathbb{R}^d, k = 1,2, \cdots, N$ と、与えられたカーネル関数 $\mathscr{K}(\cdot) = K (\lVert \cdot \rVert_2), \; \pmb{x} \in \mathbb{R}^d$ に対して、これは偶数で実数の単変数関数であり、少なくとも $\mathbb{R} \setminus \{ 0 \}$ で無限回微分可能です。もし $K$ がゼロでも無限回微分可能であれば、$\mathscr{K}$ は $\mathbb{R}^d$ 上で定義され、特異でないカーネル関数と呼ばれます。評価は $M$ 個の異なる点 $\pmb{y}_j \in \mathbb{R}^d, j = 1, \cdots, M$ で行われます。

# フィールド

  * `d` - 次元。
  * `N` - ソースノードの数。
  * `M` - ターゲットノードの数。
  * `n` - 拡張次数。
  * `p` - 平滑度の次数。
  * `kernel` - カーネル関数 $K$ の名前、[サポートされているカーネル関数](# Supported kernel functions)を参照。
  * `c` - カーネルパラメータ。
  * `eps_I` - 内部境界。
  * `eps_B` - 外部境界。
  * `nn_x` - x におけるオーバーサンプリングされた nn。
  * `nn_y` - y におけるオーバーサンプリングされた nn。
  * `m_x` - x における NFFT カットオフ。
  * `m_y` - y における NFFT カットオフ。
  * `init_done` - プラン初期化のための bool。
  * `finalized` - ファイナライザのための bool。
  * `flags` - フラグ。
  * `x` - $\lVert \pmb{x}_k \rVert_2 \leq \frac{1}{2} \ (\frac{1}{2} - \varepsilon_B)$ を満たすソースノード。
  * `y` - $\lVert \pmb{y}_k \rVert_2 \leq \frac{1}{2} \ (\frac{1}{2} - \varepsilon_B)$ を満たすターゲットノード。
  * `alpha` - ソース係数。
  * `f` - ターゲット評価。
  * `plan` - プラン (C ポインタ)。

# コンストラクタ

```
FASTSUM( d::Integer, N::Integer, M::Integer, n::Integer, p::Integer, kernel::String, c::Vector{<:Real}, eps_I::Real, eps_B::Real, nn_x::Integer, nn_y::Integer, m_x::Integer, m_y::Integer, flags::UInt32 )
```

# 追加コンストラクタ

```
FASTSUM( d::Integer, N::Integer, M::Integer, n::Integer, p::Integer, kernel::String, c::Real, eps_I::Real, eps_B::Real, nn::Integer, m::Integer )
```

# 参照

[`NFFT`](@ref)
