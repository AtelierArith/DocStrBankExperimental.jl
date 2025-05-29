```julia
applychannel(Φ, ρ)

```

  * `Φ`: ベクトルのリスト。
  * `ρ`: 入力行列。

チャネル `Φ` を `ρ` に適用した結果を返します。量子チャネル $\Phi$ のクラウス表現は、$\mathcal{H}$ 上の有界演算子の集合 $\{K_i\}_{i\in I}$ であり、$\sum_{i\in I} K_i^\dagger K_i = \mathcal{1}$ です。したがって、$\Phi(\rho)=\sum_{i\in I} K_i \rho K_i^\dagger$ です。
