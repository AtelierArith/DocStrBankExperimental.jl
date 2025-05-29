```julia
struct Hamiltonian{E<:BaytesMCMC.KineticEnergy, D<:BaytesDiff.DiffObjective}
```

運動エネルギーと対数ターゲット密度関数を保持するハミルトニアン構造体。

# フィールド

  * `K::BaytesMCMC.KineticEnergy`: 運動エネルギーの仕様。
  * `objective::BaytesDiff.DiffObjective`: モデルの微分可能な対数ターゲット密度、BaytesDiffを参照。
