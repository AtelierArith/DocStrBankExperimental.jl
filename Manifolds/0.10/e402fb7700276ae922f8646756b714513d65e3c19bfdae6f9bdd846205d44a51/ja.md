```
change_representer(::SymplecticMatrices, ::EuclideanMetric, p, X)
change_representer!(::SymplecticMatrices, Y, ::EuclideanMetric, p, X)
```

接ベクトル $ξ ∈ T_p\mathrm{Sp}(2n, ℝ)$ の表現を計算します。

$$
  g_p(c_p(ξ), η) = ⟨ξ, η⟩^{\text{Euc}} \text{for all } η ∈ T_p\mathrm{Sp}(2n, ℝ).
$$

変換関数を用いて

$$
  c_p : T_p\mathrm{Sp}(2n, ℝ) → T_p\mathrm{Sp}(2n, ℝ), \quad
  c_p(ξ) = \frac{1}{2} pp^{\mathrm{T}} ξ + \frac{1}{2} pJ_{2n} ξ^{\mathrm{T}} pJ_{2n},
$$

ここで $J_{2n} = \begin{bmatrix} 0_n & I_n \\ -I_n & 0_n \end{bmatrix}$ は [`SymplecticElement`](@ref) を示します。

上記の $c_p(η)$ の定義からの各項 $c_p^1(ξ) = p p^{\mathrm{T}} ξ$ と $c_p^2(ξ) = pJ_{2n} ξ^{\mathrm{T}} pJ_{2n}$ は、それ自体が次の意味でメトリック互換です。

$$
    c_p^i : T_p\mathrm{Sp}(2n, ℝ) → ℝ^{2n×2n}\quad
    g_p^i(c_p(ξ), η) = ⟨ξ, η⟩^{\text{Euc}} \;∀\; η ∈ T_p\mathrm{Sp}(2n, ℝ),
$$

$$
i \in {1, 2}
$$

の場合。ただし、各関数の範囲は単独では $T_p\mathrm{Sp}(2n, ℝ)$ に制限されていませんが、凸結合

$$
    c_p(ξ) = \frac{1}{2}c_p^1(ξ) + \frac{1}{2}c_p^2(ξ)
$$

は正しい範囲 $T_p\mathrm{Sp}(2n, ℝ)$ を持ちます。
