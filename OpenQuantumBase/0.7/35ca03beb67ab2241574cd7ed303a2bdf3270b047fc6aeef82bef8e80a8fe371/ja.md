```julia
mutable struct Annealing{constant_hamiltonian} <: OpenQuantumBase.AbstractAnnealing{constant_hamiltonian}
```

`Annealing`型は、閉じた系と開いた系の設定の両方における時間依存ハミルトニアンの進化を定義します。これは、HOQSTが量子アニーリングのためのツールボックスとして始まったため、`Annealing`と呼ばれています。

# フィールド

  * `H`: アニーリングのためのハミルトニアン。
  * `u0`: アニーリングのための初期状態。
  * `annealing_parameter`: tに対するアニーリングパラメータsの関数
  * `interactions`: システムバス相互作用のセット。
