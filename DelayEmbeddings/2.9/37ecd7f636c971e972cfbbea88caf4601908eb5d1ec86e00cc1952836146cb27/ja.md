```
beta_statistic(Y::StateSpaceSet, s::Vector) [, τs, w]) → β
```

入力状態空間軌道 `Y` と時系列 `s` に対して、Nichkawde [^Nichkawde2013] に基づいて、投影された多様体上での導関数の推定に基づいて β-統計量 `β` を計算します。遅延値 `τs` の範囲に対して、`β` が計算され、考慮されたすべての `τs` の中での最大値がこの埋め込みサイクルで考慮される最適な遅延として機能します。

引数 `τs, w` は [`mdop_embedding`](@ref) と同様です。

## 説明

`β`-統計量は、再構成されたアトラクタの最大展開の幾何学的アイデアに基づいており、偽近隣法 ([^Kennel1992]) に密接に関連しています。実際、この方法は各埋め込みサイクルで最大限の偽近隣を排除します。アイデアは、再構成プロセスにおける可能な新しい次元に関する方向導関数の絶対値を、状態空間軌道のすべての点に対して、最近傍に関して推定することです。

ϕ'(τ) = Δϕ*d(τ) / Δx*d

Δx*d は、与えられた Theiler ウィンドウ `w` に関する参照点のユークリッド最近傍距離です。Δϕ*d(τ) は、特定の τ に対して、参照点からその最近傍までの距離です。Δϕ_d(τ) = |s(i+τ)-s(j+τ)| で、i は考慮された参照点のインデックス、j はその最近傍のインデックスです。

最後に、

`β` = log β(τ) = ⟨log₁₀ ϕ'(τ)⟩ ,

ここで ⟨.⟩ はすべての参照点の平均です。考慮されたすべての τ の中で `β` の最大値を選択すると、この埋め込みサイクルの最適な遅延値が得られます。最初の埋め込みサイクルでは、入力状態空間軌道 `Y` は単変量時系列であることもあります。

[^Nichkawde2013]: Nichkawde, Chetan (2013). [Optimal state-space reconstruction using derivatives on projected manifold. Physical Review E 87, 022905](https://doi.org/10.1103/PhysRevE.87.022905).

[^Kennel1992]: Kennel, M. B., Brown, R., Abarbanel, H. D. I. (1992). [Determining embedding dimension for state-space reconstruction using a geometrical construction. Phys. Rev. A 45, 3403](https://doi.org/10.1103/PhysRevA.45.3403).
