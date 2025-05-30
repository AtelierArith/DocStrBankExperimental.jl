```
RydbergChainSystem(;
    N::Int=3, # 原子の数
    C::Float64=862690*2π,
    distance::Float64=10.0, # μm
    cutoff_order::Int=2, # 1は最近接隣接、2は次最近接隣接、など。
    local_detune::Bool=false, # trueの場合、1つの局所的なデチューンパターンを含める。
    all2all::Bool=true, # trueの場合、全ての相互作用を含める。
    ignore_Y_drive::Bool=false, # trueの場合、Yドライブを無視する。(実験では、X&Yドライブはラビ振幅とその位相によって実装される。)
) -> QuantumSystem
```

Rydberg原子チェーンのスピン基底における`QuantumSystem`オブジェクトを返します     |g⟩ = |0⟩ = [1, 0], |r⟩ = |1⟩ = [0, 1].

$$
H = \sum_i 0.5*\Omega_i(t)\cos(\phi_i(t)) \sigma_i^x - 0.5*\Omega_i(t)\sin(\phi_i(t)) \sigma_i^y - \sum_i \Delta_i(t)n_i + \sum_{i<j} \frac{C}{|i-j|^6} n_i n_j
$$

# キーワード引数

  * `N`: 原子の数。
  * `C`: Rydberg相互作用の強さ（MHz*μm^6）。
  * `distance`: 原子間の距離（μm）。
  * `cutoff_order`: 相互作用範囲のカットオフ、1は最近接隣接、2は次最近接隣接。
  * `local_detune`: trueの場合、1つの局所的なデチューンパターンを含める。
  * `all2all`: trueの場合、全ての相互作用を含める。
  * `ignore_Y_drive`: trueの場合、Yドライブを無視する。(実験では、X&Yドライブはラビ振幅とその位相によって実装される。)
