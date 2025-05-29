```
FermionGreensCalculator{T<:Continuous, E<:AbstractFloat}
```

単一粒子フェルミオン・グリーン関数行列を計算するための型です。

# フィールド

  * `forward::Bool`: `true` の場合、$l=1$ から $l=L_\tau$ までの虚時間スライスを反復します。`false` の場合、$l=L_\tau$ から $l=1$ までの虚時間スライスを反復します。
  * `l::Int`: 現在の虚時間スライス $\tau = l \cdot \Delta\tau$。
  * `n_stab::Int`: 数値的安定化が行われる頻度、すなわち、$n_s$ 個の虚時間スライスごとに等時グリーン関数が最初から再計算されます。
  * `N_stab::Int`: 数値的安定化の間隔の数、$N_s = \left\lceil L_\tau / n_s \right\rceil.$
  * `N::Int`: 系の軌道。
  * `β::E`: 逆温度 $\beta=1/T,$ ここで $T$ は温度です。
  * `Δτ::E`: 虚時間の離散化。
  * `Lτ::Int`: 虚時間軸の長さ、$L_\tau = \beta / \Delta\tau.$
  * `B_bar::Vector{Matrix{T}}`: 行列 `B_bar[:,:,n]` が $\bar{B}_n.$ を表す多次元配列です。
  * `F::Vector{LDR{T,E}}`: 行列 $B(0,\tau)$ と $B(\tau,\beta)$ を表す $N_s$ の LDR因子分解のベクトルです。
  * `G′::Matrix{T}`: 等時グリーン関数の数値的安定化によって修正された誤差を計算するために使用される行列です。
  * `ldr_ws::LDRWorkspace{T}`: 動的メモリ割り当てを避けながら LDR因子分解を行うためのワークスペースです。
