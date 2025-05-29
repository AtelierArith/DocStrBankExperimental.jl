```
local_update_det_ratio(
    G::AbstractMatrix,
    B::AbstractPropagator,
    V′::T, i::Int, Δτ::E
) where {T<:Number, E<:AbstractFloat}
```

局所更新に関連する行列式比 $R_{l,i}$ を計算します。これは等時グリーン関数 $G(\tau,\tau)$ への更新です。また、以下に定義される $\Delta_{l,i}$ も返します。具体的には、この関数はタプル $(R_{l,i}, \Delta_{l,i})$ を返します。

# 引数

  * `G::AbstractMatrix`: 等時グリーン関数行列 $G(\tau,\tau)$。
  * `B::AbstractPropagator`: $\tau = \Delta\tau \cdot l$ の propagator 行列 $B_l$ を表します。
  * `V′::T`: 対角のオンサイトエネルギー行列 $V_l$ の新しい値 $V^{\prime}_{l,i,i}$ 行列要素。
  * `i::Int`: 更新される $V_l$ の対角行列要素インデックス。
  * `Δτ::E`: 虚時間の離散化 $\Delta\tau$。

# アルゴリズム

上記の propagator 行列 $B_l$ は次のように与えられます。

$$
B_l = \Lambda_l \cdot \Gamma_l(\Delta\tau),
$$

ここで、軌道基底で作業していると仮定すると、$\Gamma_l(\Delta\tau) = e^{-\Delta\tau K_l}$ は指数化されたホッピング行列 $K_l$ を表し、$\Lambda_l = e^{-\Delta\tau V_l}$ は指数化された対角のオンサイトエネルギー行列 $V_l$ を表します。

対角のオンサイトエネルギー行列 $V_l$ の $(i,i)$ 行列要素への提案された更新 ($V_{l,i,i} \rightarrow V^\prime_{l,i,i})$ に対して、この提案された更新に関連する行列式比は次のように与えられます。

$$
R_{l,i} = \frac{\det G(\tau,\tau)}{\det G^\prime(\tau,\tau)} = 1+\Delta_{i,i}(\tau,i)\left(1-G_{i,i}(\tau,\tau)\right),
$$

ここで

$$
\Delta_{l,i} = \frac{\Lambda^\prime_{l,i,i}}{\Lambda_{l,i,i}} - 1 = e^{-\Delta\tau (V^\prime_{l,i,i} - V_{l,i,i})} - 1.
$$

このルーチンはスカラー量 $R_{l,i}$ と $\Delta_{l,i}$ を返します。

propagator 行列が対称形を使用して表される場合

$$
B_l = \Gamma_l(\Delta\tau/2) \cdot \Lambda_l \cdot \Gamma^\dagger_l(\Delta\tau/2),
$$

その場合、行列 `G` は変換された等時グリーン関数行列を表す必要があります。

$$
\tilde{G}(\tau,\tau) = \Gamma_l^{-1}(\Delta\tau/2) \cdot G(\tau,\tau) \cdot \Gamma_l(\Delta\tau/2).
$$

```
