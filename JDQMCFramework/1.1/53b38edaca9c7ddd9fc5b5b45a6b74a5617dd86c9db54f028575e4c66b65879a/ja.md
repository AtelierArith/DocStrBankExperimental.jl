```
partially_wrap_greens_forward!(
    G::Matrix{T},
    B::P,
    M::Matrix{T} = similar(G)
) where {T, E, P<:AbstractPropagator{T,E}}
```

もし伝播子 `B` が対称形で表されるなら

$$
B_l = \Gamma_l(\Delta\tau/2) \cdot \Lambda_l(\Delta\tau) \cdot \Gamma_l^\dagger(\Delta\tau/2)
$$

ここで $\tau = l \cdot \Delta\tau,$ かつ $\Gamma(\Delta\tau/2) = e^{-\Delta\tau K_l/2}$ および $\Lambda(\Delta\tau) = e^{-\Delta\tau V_l}$ であるとき、次の変換を適用します。

$$
\tilde{G}(\tau,\tau) = \Gamma^{-1}_l(\Delta\tau/2) \cdot G(\tau,\tau) \cdot \Gamma_l(\Delta\tau/2)
$$

等時グリーン関数行列 `G` に対してインプレースで。
