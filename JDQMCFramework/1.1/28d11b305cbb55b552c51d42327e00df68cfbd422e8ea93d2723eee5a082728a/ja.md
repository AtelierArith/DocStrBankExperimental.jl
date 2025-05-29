```
calculate_equaltime_greens!(
    G::AbstractMatrix{T},
    fgc::FermionGreensCalculator{T,E},
    B::AbstractVector{P}
)::Tuple{E,T} where {T, E, P<:AbstractPropagator{T}}
```

等時グリーン関数 $G(0,0) = G(\beta,\beta) = [I + B(\beta,0)]^{-1}$ を数値的に安定した手法を用いて計算します。また、`fgc.F` に保存されている $B(\tau,0)$ または $B(\beta,\tau)$ を表す $\bar{B}_n$ 行列と LDR 行列因子分解を再計算します。このルーチンは、すべての伝播子行列 $B_l$ が変更されたグローバル更新を実装するのに便利で、等時グリーン関数を最初から再計算する必要があります。このメソッドはまた、$\log(\vert \det G \vert)$ と $\textrm{sign}(\det G)$ を返します。このルーチンは `fgc.l == 1` または `fgc.l == fgc.Lτ` を必要とすることに注意してください。
