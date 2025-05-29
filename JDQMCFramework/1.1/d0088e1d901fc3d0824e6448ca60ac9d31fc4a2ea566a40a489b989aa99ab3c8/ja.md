```
stabilize_unequaltime_greens!(
    Gτ0::AbstractMatrix{T},
    G0τ::AbstractMatrix{T},
    Gττ::AbstractMatrix{T},
    logdetG::E, sgndetG::T,
    fgc::FermionGreensCalculator{T,E},
    B::AbstractVector{P};
    # KEYWORD ARGUMENTS
    update_B̄::Bool=true
)::Tuple{E,T,E,E} where {T, E, P<:AbstractPropagator{T}}
```

グリーン関数行列 $G(\tau,0)$、$G(0,\tau)$、および $G(\tau,\tau)$ を、虚時間 $\tau = \Delta\tau \cdot l$ を通じて反復することで安定化します。与えられた虚時間スライス `fgc.l` に対して、このルーチンは $B_l$ 漸近子に対するすべての変更が行われた *後* に呼び出されるべきです。虚時間を前方方向に反復する場合（`fgc.forward = true`）、この関数は再計算します。

$$
\begin{align}
G(\tau,0)    = & [B^{-1}(\tau,0) + B(\beta,\tau)]^{-1} \\
G(0, \tau)   = & [B^{-1}(\beta,\tau) + B(\tau,0)]^{-1} \\
G(\tau,\tau) = & [I + B(\tau,0)B(\beta,\tau)]^{-1}
\end{align}
$$

虚時間スライス `fgc.l` において、すべての `fgc.n_stab` 虚時間スライスで。虚時間を逆方向に反復する場合（`fgc.forward = false`）、この関数は代わりに再計算します。

$$
\begin{align*}
G(\tau-\Delta\tau,0)               = & [B^{-1}(\tau-\Delta\tau,0) + B(\beta,\tau-\Delta\tau)]^{-1} \\
G(0,\tau-\Delta\tau)               = & [B^{-1}(\beta,\tau-\Delta\tau) + B(\tau-\Delta\tau,0)]^{-1} \\
G(\tau-\Delta\tau,\tau-\Delta\tau) = & [I + B(\tau-\Delta\tau,0)B(\beta,\tau-\Delta\tau)]^{-1}
\end{align*}
$$

`fgc.l` に対して。

このメソッドは4つの値を返します。最初の2つの値は $\log(\vert \det G(\tau,\tau) \vert)$ と $\textrm{sign}(\det G(\tau,\tau))$ です。後の2つは、数値的安定化によって修正されたグリーン関数の最大誤差 $\vert \delta G \vert$ と、数値的安定化によって修正された行列式の位相の誤差 $\delta\theta$ であり、虚時間におけるグリーン関数行列の単純な伝播に対して相対的です。安定化が行われなかった場合、$\vert \delta G \vert = 0$ および $\delta \theta = 0$ となります。

このメソッドはまた、虚時間 $\tau = \Delta\tau \cdot l$ を前方および逆方向に反復する際に、$B(\tau, 0)$ または $B(\beta, \tau-\Delta\tau)$ を表す LDR 行列因子分解を計算します。`update_B̄ = true` の場合、$\bar{B}_n$ 行列は必要に応じて再計算されますが、`update_B̄ = false` の場合は変更されません。
