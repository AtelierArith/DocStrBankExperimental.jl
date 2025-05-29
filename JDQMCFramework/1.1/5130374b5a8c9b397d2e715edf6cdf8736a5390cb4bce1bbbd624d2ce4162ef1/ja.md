```
propagate_equaltime_greens!(
    G::AbstractMatrix{T},
    fgc::FermionGreensCalculator{T,E},
    B::AbstractVector{P}
) where {T, E, P<:AbstractPropagator{T}}
```

前の虚時間スライスから現在の虚時間スライス `fgc.l` へ等時グリーン関数行列 `G` を伝播させます。虚時間を前方方向に反復している場合（`fgc.forward = true`）、次の関係式が使用されます。

$$
G(\tau+\Delta\tau,\tau+\Delta\tau) = B_{l+1} \cdot G(\tau,\tau) \cdot B_{l+1}^{-1}
$$

逆方向に虚時間を反復している場合（`fgc.forward = false`）、次の関係式が代わりに使用されます。

$$
G(\tau-\Delta\tau,\tau-\Delta\tau)= B_{l}^{-1} \cdot G(\tau,\tau) \cdot B_{l}
$$

ここで、$B_l$ 演算子は `B[l]` で与えられます。
