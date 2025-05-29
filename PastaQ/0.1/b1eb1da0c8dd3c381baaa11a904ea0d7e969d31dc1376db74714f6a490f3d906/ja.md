```
runcircuit(
  M::Union{MPS,MPO},
  circuit_tensors::Vector{<:ITensor};
  apply_dag=nothing,
  cutoff=1e-15,
  maxdim=10_000,
  svd_alg="divide_and_conquer",
  move_sites_back::Bool=true,
  kwargs...)
```

入力状態 `M` に対して「ゲート」テンソル（すでに `ITensor` の形式である）を適用します。オプションは次のとおりです：

  * `apply_dag = nothing`: 共役進化を行うかどうか。
  * `cutoff = 1e-15`: SVD における切断カットオフ。
  * `maxdim = 10_000`: SVD 切断時の最大ボンド次元。
  * `svd_alg = "divide_and_conquer"`: SVD アルゴリズム（ITensors.jl を参照）。
  * `move_sites_back = true`: 長距離ゲートの後にサイトを戻す。

デフォルトでは、`apply_dag = nothing` であり、インターフェースは入力状態によって決定され、`ITensor` のベクトルがランク3のノイズのあるテンソル（すなわち、クラウス演算子）を含むかどうかによります。

入力 MPS $|\psi_0\rangle$ に対して、ユニタリー回路を用いると、出力は

$$
|\psi\rangle = U_M\dots U_2 U_1|\psi_0\rangle
$$

ノイズのある回路の場合は：

$$
\rho = \mathcal{E}(|\psi_0\rangle\langle\psi_0|)
$$

入力 MPO $\rho_0$ に対して、出力は

$$
\rho = U_M\dots U_2 U_1 \rho_0 U^\dagger_1 U^\dagger_2,\dots,U^\dagger_M
$$

ユニタリー回路の場合、ノイズのある回路の場合は $\rho = \mathcal{E}(\rho_0)$ です。
