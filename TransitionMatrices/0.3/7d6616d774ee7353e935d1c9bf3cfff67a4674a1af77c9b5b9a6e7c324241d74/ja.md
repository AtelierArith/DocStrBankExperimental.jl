```
scattering_matrix(α₁, α₂, α₃, α₄, β₁, β₂, β₃, β₄, β₅, β₆, θs)
```

与えられた展開係数からすべての10の独立した散乱行列要素（`F₁₁`, `F₁₂`, `F₁₃`, `F₁₄`, `F₂₂`, `F₂₃`, `F₂₄`, `F₃₃`, `F₃₄`, `F₄₄`）を計算します。

散乱行列は次のように表現できます：

$$
\mathbf{F}=\left[\begin{array}{cccc}
F_{11} & F_{12} & F_{13} & F_{14} \\
F_{12} & F_{22} & F_{23} & F_{24} \\
-F_{13} & -F_{23} & F_{33} & F_{34} \\
F_{14} & F_{24} & -F_{34} & F_{44}
\end{array}\right]
$$

パラメータ：

  * `α₁`, `α₂`, `α₃`, `α₄`, `β₁`, `β₂`, `β₃`, `β₄`, `β₅`, `β₆`: 事前計算された展開係数。
  * `θs`: 評価される散乱角度（度単位）。
