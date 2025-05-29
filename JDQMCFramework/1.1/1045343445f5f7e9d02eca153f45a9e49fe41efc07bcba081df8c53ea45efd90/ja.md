```
stabilize_equaltime_greens!(
    G::AbstractMatrix{T},
    logdetG::E, sgndetG::T,
    fgc::FermionGreensCalculator{T,E},
    B::AbstractVector{P};
    # KEYWORD ARGUMENTS
    update_B̄::Bool=true
)::Tuple{E,T,E,E} where {T, E, P<:AbstractPropagator{T}}
```

等時間グリーン関数を安定化します。虚時間 $\tau = \Delta\tau \cdot l.$ を通じて反復する際に、与えられた虚時間スライス `fgc.l` に対して、このルーチンは $B_l$ 演算子へのすべての変更が行われた *後* に呼び出されるべきです。虚時間を前方方向に反復する場合（`fgc.forward = true`）、この関数は次を再計算します。

$$
G(\tau,\tau) = [I + B(\tau,0)B(\beta,\tau)]^{-1}
$$

虚時間スライス `fgc.l` において、すべての `fgc.n_stab` 虚時間スライスで。虚時間を逆方向に反復する場合（`fgc.forward = false`）、この関数は代わりに次を再計算します。

$$
G(\tau-\Delta\tau,\tau-\Delta\tau) = [I + B(\tau-\Delta\tau,0)B(\beta,\tau-\Delta\tau)]^{-1}
$$

`fgc.l` に対して。

このメソッドは4つの値を返します。最初の2つの値は $\log(\vert \det G(\tau,\tau) \vert)$ と $\textrm{sign}(\det G(\tau,\tau))$ です。後の2つは数値的安定化によって修正されたグリーン関数の最大誤差 $\vert \delta G \vert$ と、数値的安定化によって修正された行列式の位相の誤差 $\delta\theta$ であり、代わりに虚時間におけるグリーン関数行列の単純な伝播が発生します。安定化が行われなかった場合、$\vert \delta G \vert = 0$ および $\delta \theta = 0$ となります。

このメソッドはまた、虚時間 $\tau = \Delta\tau \cdot l$ を通じて前方および逆方向に反復する際に $B(\tau, 0)$ または $B(\beta, \tau-\Delta\tau)$ を表すLDR行列因子分解を計算します。`update_B̄ = true` の場合、必要に応じて $\bar{B}_n$ 行列が再計算されますが、`update_B̄ = false` の場合は変更されません。
