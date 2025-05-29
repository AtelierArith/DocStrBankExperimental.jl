```
calculate_equaltime_greens!(
    G::AbstractMatrix{T},
    fgc::FermionGreensCalculator{T,E}
)::Tuple{E,T} where {T,E}
```

等時グリーン関数 $G(0,0) = G(\beta,\beta) = [I + B(\beta,0)]^{-1}$ を数値的に安定した手法を用いて計算します。この方法はまた $\log(\vert \det G \vert)$ と $\textrm{sign}(\det G)$ を返します。このルーチンは `fgc.l == 1` または `fgc.l == fgc.Lτ` を必要とすることに注意してください。
