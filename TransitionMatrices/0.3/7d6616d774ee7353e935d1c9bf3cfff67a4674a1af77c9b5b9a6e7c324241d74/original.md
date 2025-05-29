```
scattering_matrix(α₁, α₂, α₃, α₄, β₁, β₂, β₃, β₄, β₅, β₆, θs)
```

Calculate all 10 independent scatterering matrix elements (`F₁₁`, `F₁₂`, `F₁₃`, `F₁₄`, `F₂₂`, `F₂₃`, `F₂₄`, `F₃₃`, `F₃₄`, `F₄₄`) from the given expansion coefficients.

The scattering matrix can be expressed as:

$$
\mathbf{F}=\left[\begin{array}{cccc}
F_{11} & F_{12} & F_{13} & F_{14} \\
F_{12} & F_{22} & F_{23} & F_{24} \\
-F_{13} & -F_{23} & F_{33} & F_{34} \\
F_{14} & F_{24} & -F_{34} & F_{44}
\end{array}\right]
$$

Parameters:

  * `α₁`, `α₂`, `α₃`, `α₄`, `β₁`, `β₂`, `β₃`, `β₄`, `β₅`, `β₆`: The precalculated expansion coefficients.
  * `θs`: The scattering angles to be evaluated in degrees.
