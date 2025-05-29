```
init_plus_phase_state!(phase::Phase, qureg, qᵢ, φᵢ)
```

この関数は、指定された位相を持つ重ね合わせ状態（|+⟩状態）に量子状態を初期化します。最初に、量子ビットにハダマードゲートを適用し、重ね合わせ状態にします。次に、量子ビットにZ回転を適用し、指定された位相を追加します。

# 引数

  * `phase::Phase`: 位相オブジェクト。
  * `qureg`: 量子ビットを含む量子レジスタ。
  * `qᵢ`: 量子レジスタ内の量子ビットのインデックス。
  * `φᵢ`: 量子ビットに追加される位相。

# 例

```julia
phase = Phase()
qureg = createQureg(1, env)
qᵢ = 1
φᵢ = π/2
init_plus_phase_state!(phase, qureg, qᵢ, φᵢ)
```
