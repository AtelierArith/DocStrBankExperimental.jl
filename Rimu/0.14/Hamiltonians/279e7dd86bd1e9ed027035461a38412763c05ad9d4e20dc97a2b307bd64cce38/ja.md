```
HOCartesianCentralImpurity(addr; kwargs...)
```

中心にデルタ関数ポテンシャルを持つ任意の調和トラップ内の非相互作用粒子のハミルトニアンで、強さ `g` を持つ、

$$
\hat{H}_\mathrm{rel} = \sum_\mathbf{i} ϵ_\mathbf{i} n_\mathbf{i}
    + g\sum_\mathbf{ij} V_\mathbf{ij} a^†_\mathbf{i} a_\mathbf{j}.
$$

$$
D
$$

次元の調和振動子に対して、インデックス $\mathbf{i}, \mathbf{j}, \ldots$ は $D$-タプルです。エネルギースケールは最初の次元、すなわち $\hbar \omega_x$ によって定義されるため、単一粒子のエネルギーは

$$
    \frac{\epsilon_\mathbf{i}}{\hbar \omega_x} = (i_x + 1/2) + \eta_y (i_y+1/2) + \ldots.
$$

因子 $\eta_y, \ldots$ は異方的なトラッピング幾何学を許可し、$\omega_x$ が最小のトラッピング周波数となるように `1` より大きいと仮定されます。

行列要素 $V_{\mathbf{ij}}$ は、この基底で計算されたデルタ関数ポテンシャルのためのもので、

$$
    V_{\mathbf{ij}} = \prod_{d \in x, y,\ldots} \psi_{i_d}(0) \psi_{j_d}(0).
$$

偶数パリティ状態のみがこの不純物を感じるため、すべての $i_d$ は偶数です。このハミルトニアンの単一粒子の行列表現は、偶数パリティサブスペース内で完全に密です。

# 引数

  * `addr`: 開始アドレス、粒子の数とモードの総数を定義します。
  * `max_nx = num_modes(addr) - 1`: $x$-次元における最大調和振動子インデックス番号。偶数でなければなりません。調和振動子の基底状態のインデックス番号は `0` です。
  * `ηs = ()`: 残りの次元のアスペクト比のタプル `(η_y, ...)`。1Dトラップの場合は空であるべきで、`1.0` より大きい値を含むべきです。他の次元での最大インデックスは、$M/η_y$ より小さい最大の偶数になります。
  * `S = nothing`: `max_nx` の代わりに、基底状態を含む各次元のレベル数を手動で設定します。`Int` の `Tuple` でなければなりません。
  * `g = 1.0`: ($x$-次元) トラップ単位におけるデルタ不純物の強さ。
  * `impurity_only=false`: `true` に設定すると、トラップエネルギー項は無視されます。不純物によるエネルギーシフトのみが必要な場合に便利です。

!!! warning
    ```
    大きな引数を持つ `SpecialFunctions` の使用により、このハミルトニアンの行列表現は厳密に対称ではない可能性がありますが、機械精度内でおおよそ対称です。
    ```


他に [`HOCartesianContactInteractions`](@ref) と [`HOCartesianEnergyConservedPerDim`](@ref) を参照してください。
