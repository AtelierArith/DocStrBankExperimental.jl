```
exp(::SymplecticStiefel, p, X)
exp!(M::SymplecticStiefel, q, p, X)
```

Compute the exponential mapping

$$
  \exp\colon T\mathrm{SpSt}(2n, 2k) → \mathrm{SpSt}(2n, 2k)
$$

at a point $p ∈ \mathrm{SpSt}(2n, 2k)$ in the direction of $X ∈ T_p\mathrm{SpSt}(2n, 2k)$.

The tangent vector $X$ can be written in the form $X = \bar{\Omega}p$ [BendokatZimmermann:2021](@cite), with

$$
  \bar{\Omega} = X (p^{\mathrm{T}}p)^{-1}p^{\mathrm{T}}
    + J_{2n}p(p^{\mathrm{T}}p)^{-1}X^{\mathrm{T}}(I_{2n}
    - J_{2n}^{\mathrm{T}}p(p^{\mathrm{T}}p)^{-1}p^{\mathrm{T}}J_{2n})J_{2n}
    ∈ ℝ^{2n×2n},
$$

where $J_{2n} = \begin{bmatrix} 0_n & I_n \\ -I_n & 0_n \end{bmatrix}$ denotes the [`SymplecticElement`](@ref).

Using this expression for $X$, the exponential mapping can be computed as

$$
  \exp_p(X) = \operatorname{Exp}([\bar{\Omega} - \bar{\Omega}^{\mathrm{T}}])
                             \operatorname{Exp}(\bar{\Omega}^{\mathrm{T}})p,
$$

where $\operatorname{Exp}(⋅)$ denotes the matrix exponential.

Computing the above mapping directly however, requires taking matrix exponentials of two $2n×2n$ matrices, which is computationally expensive when $n$ increases. Therefore we instead follow [BendokatZimmermann:2021](@cite) who express the above exponential mapping in a way which only requires taking matrix exponentials of an $8k×8k$ matrix and a $4k×4k$ matrix.

To this end, first define

$$
\bar{A} = J_{2k}p^{\mathrm{T}}X(p^{\mathrm{T}}p)^{-1}J_{2k} +
            (p^{\mathrm{T}}p)^{-1}X^{\mathrm{T}}(p - J_{2n}^{\mathrm{T}}p(p^{\mathrm{T}}p)^{-1}J_{2k}) ∈ ℝ^{2k×2k},
$$

and

$$
\bar{H} = (I_{2n} - pp^+)J_{2n}X(p^{\mathrm{T}}p)^{-1}J_{2k} ∈ ℝ^{2n×2k}.
$$

We then let $\bar{\Delta} = p\bar{A} + \bar{H}$, and define the matrices

$$
    γ = \left[\left(I_{2n} - \frac{1}{2}pp^+\right)\bar{\Delta} \quad
              -p \right] ∈ ℝ^{2n×4k},
$$

and

$$
    λ = \left[J_{2n}^{\mathrm{T}}pJ_{2k} \quad
        \left(\bar{\Delta}^+\left(I_{2n}
              - \frac{1}{2}pp^+\right)\right)^{\mathrm{T}}\right] ∈ ℝ^{2n×4k}.
$$

With the above defined matrices it holds that $\bar{\Omega} = λγ^{\mathrm{T}}$.  As a last preliminary step, concatenate $γ$ and $λ$ to define the matrices $Γ = [λ \quad -γ] ∈ ℝ^{2n×8k}$ and $Λ = [γ \quad λ] ∈ ℝ^{2n×8k}$.

With these matrix constructions done, we can compute the exponential mapping as

$$
  \exp_p(X) = Γ \operatorname{Exp}(ΛΓ^{\mathrm{T}})
    \begin{bmatrix} 0_{4k} \\ I_{4k} \end{bmatrix}
    \operatorname{Exp}(λγ^{\mathrm{T}})
    \begin{bmatrix} 0_{2k} \\ I_{2k} \end{bmatrix}.
$$

which only requires computing the matrix exponentials of $ΛΓ^{\mathrm{T}} ∈ ℝ^{8k×8k}$ and $λγ^{\mathrm{T}} ∈ ℝ^{4k×4k}$.
