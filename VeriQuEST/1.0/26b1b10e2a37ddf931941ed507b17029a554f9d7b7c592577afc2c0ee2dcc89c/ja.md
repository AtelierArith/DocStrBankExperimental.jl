```
init_plus_phase_state!(nophase::NoPhase, qureg, qᵢ)
```

この関数は、位相を追加せずに量子状態を重ね合わせ状態（|+⟩状態）に初期化します。キュービットにハダマードゲートを適用し、重ね合わせ状態にします。

# 引数

  * `nophase::NoPhase`: 位相を追加しないことを示すNoPhaseオブジェクト。
  * `qureg`: キュービットを含む量子レジスタ。
  * `qᵢ`: 量子レジスタ内のキュービットのインデックス。

# 例

```julia
nophase = NoPhase()
qureg = createQureg(1, env)
qᵢ = 1
init_plus_phase_state!(nophase, qureg, qᵢ)
```
