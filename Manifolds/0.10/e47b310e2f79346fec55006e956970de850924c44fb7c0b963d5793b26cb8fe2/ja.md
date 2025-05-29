```
exp(::SymplecticStiefel, p, X)
exp!(M::SymplecticStiefel, q, p, X)
```

指数写像を計算します

$$
  \exp\colon T\mathrm{SpSt}(2n, 2k) → \mathrm{SpSt}(2n, 2k)
$$

点 $p ∈ \mathrm{SpSt}(2n, 2k)$ において、方向 $X ∈ T_p\mathrm{SpSt}(2n, 2k)$ に沿った。

接ベクトル $X$ は、次の形で書くことができます $X = \bar{\Omega}p$ [BendokatZimmermann:2021](@cite)、ここで

$$
  \bar{\Omega} = X (p^{\mathrm{T}}p)^{-1}p^{\mathrm{T}}
    + J_{2n}p(p^{\mathrm{T}}p)^{-1}X^{\mathrm{T}}(I_{2n}
    - J_{2n}^{\mathrm{T}}p(p^{\mathrm{T}}p)^{-1}p^{\mathrm{T}}J_{2n})J_{2n}
    ∈ ℝ^{2n×2n},
$$

ここで $J_{2n} = \begin{bmatrix} 0_n & I_n \\ -I_n & 0_n \end{bmatrix}$ は [`SymplecticElement`](@ref) を示します。

この $X$ の表現を使用して、指数写像は次のように計算できます

$$
  \exp_p(X) = \operatorname{Exp}([\bar{\Omega} - \bar{\Omega}^{\mathrm{T}}])
                             \operatorname{Exp}(\bar{\Omega}^{\mathrm{T}})p,
$$

ここで $\operatorname{Exp}(⋅)$ は行列の指数を示します。

ただし、上記の写像を直接計算するには、2つの $2n×2n$ 行列の行列指数を取る必要があり、$n$ が増加すると計算コストが高くなります。したがって、代わりに [BendokatZimmermann:2021](@cite) に従い、上記の指数写像を $8k×8k$ 行列と $4k×4k$ 行列の行列指数を取るだけで済むように表現します。

この目的のために、まず次を定義します

$$
\bar{A} = J_{2k}p^{\mathrm{T}}X(p^{\mathrm{T}}p)^{-1}J_{2k} +
            (p^{\mathrm{T}}p)^{-1}X^{\mathrm{T}}(p - J_{2n}^{\mathrm{T}}p(p^{\mathrm{T}}p)^{-1}J_{2k}) ∈ ℝ^{2k×2k},
$$

および

$$
\bar{H} = (I_{2n} - pp^+)J_{2n}X(p^{\mathrm{T}}p)^{-1}J_{2k} ∈ ℝ^{2n×2k}.
$$

次に、$\bar{\Delta} = p\bar{A} + \bar{H}$ とし、行列を定義します

$$
    γ = \left[\left(I_{2n} - \frac{1}{2}pp^+\right)\bar{\Delta} \quad
              -p \right] ∈ ℝ^{2n×4k},
$$

および

$$
    λ = \left[J_{2n}^{\mathrm{T}}pJ_{2k} \quad
        \left(\bar{\Delta}^+\left(I_{2n}
              - \frac{1}{2}pp^+\right)\right)^{\mathrm{T}}\right] ∈ ℝ^{2n×4k}.
$$

上記で定義された行列に対して、$\bar{\Omega} = λγ^{\mathrm{T}}$ が成り立ちます。最後の準備段階として、$γ$ と $λ$ を連結して行列 $Γ = [λ \quad -γ] ∈ ℝ^{2n×8k}$ および $Λ = [γ \quad λ] ∈ ℝ^{2n×8k}$ を定義します。

これらの行列構成が完了したので、指数写像を次のように計算できます

$$
  \exp_p(X) = Γ \operatorname{Exp}(ΛΓ^{\mathrm{T}})
    \begin{bmatrix} 0_{4k} \\ I_{4k} \end{bmatrix}
    \operatorname{Exp}(λγ^{\mathrm{T}})
    \begin{bmatrix} 0_{2k} \\ I_{2k} \end{bmatrix}.
$$

これは、$ΛΓ^{\mathrm{T}} ∈ ℝ^{8k×8k}$ および $λγ^{\mathrm{T}} ∈ ℝ^{4k×4k}$ の行列指数を計算するだけで済みます。
